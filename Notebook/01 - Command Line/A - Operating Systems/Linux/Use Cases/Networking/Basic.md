# Basic

Search Tag(s): #command-line #networking #use-cases #linux

## Retrieve private IPv4 address

TODO: Rearrange them

```
$ ifconfig | grep "inet" | grep "broadcast" | awk '{print $2}'

$ ifconfig -a | awk '/(inet)(.*)broadcast/ {print $2}'

$ ifconfig | grep -v 127.0.0.1 | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | awk '{print $2}'

$ ip address | grep -v 127.0.0.1 | grep -Eo "(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)"

$ while read -r line; do ping -c 1 $line | grep "bytes from" | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b"; done < ips.txt | tee output.txt
```

```
$ ip -4 -o address | awk '{print $4}' | cut -d "/" -f 1

$ ip -f inet address | awk '/inet / { print $2 }'

$ ip address | awk '$1 == "inet" && $3 == "brd" { sub (/\/.*/,""); print $2 }'

$ ip address | awk -- '$1 == "inet" && $3 == "brd" { split($2,a,"/"); print a[1]; }'

$ ip address | egrep '^ *inet' | grep brd | awk -- '{ print $2; }' | sed -e 's:/[0-9]*$::'

$ awk '/32 host/ { print f } {f=$2}' /proc/net/fib_trie | sort -u
```

## Retrieve Netblocks

```
$ grep -Eo '[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}/[0-9]{1,2}' file.txt

$ grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}' file.txt
```

## Retrieve MAC Address

```
$ ip address | awk '/ether/{print $2}'

$ cat /sys/class/net/<interface>/address
```

## IP/CIDR Formatting

### Perl

```perl
!/usr/bin/perl -w

use strict;

my $target;
if ($ARGV[0] =~ m{^\d+}) {
    $target = + shift @ARGV;
}


my $map = [];

sub record($) 
{
    my $v = shift;

    my $m = $map;
    for my $i ( 0 .. 31 ) {
        my $k = $v & (1 << (31-$i));
        $m = $m->[!!$k] ||= (($i == 31) ? $v : []);
    }
}

while (<>) {
    chomp;

    if (m{^\s*(\d+)\.(\d+)\.(\d+)\.(\d+)\s*\z}) {
        if (($1 < 256) && ($2 < 256) && ($3 < 256) && ($4 < 256)) {
            record(($1<<24) | ($2<<16) | ($3 << 8) | $4);
            next;
        }
    }

    printf("Invalid: %s\n", $_);
}

sub output($$$) {
    my ($addr, $bits, $indent) = @_;
    printf "%*s%d.%d.%d.%d",
           $indent*4, '',
           0xff & ($addr >> 24),
           0xff & ($addr >> 16),
           0xff & ($addr >>  8),
           0xff & ($addr      );
    printf("/%d", $bits) if $bits < 32;
    print "\n";
}

sub walk($$$$);
sub walk($$$$) {
    my ($prefix, $bits, $indent, $m) = @_;
    #printf ("%d %d %d ...\n", $prefix, $bits, $indent);
    if ($bits == ($target//-1)) {
        output $prefix<<(32-$bits), $bits, 0;
    } elsif ($bits == 32) { 
        warn 'mismatch '.$prefix.' != '.$m unless $prefix == $m;
        output $prefix, $bits, $indent unless defined $target;
    } elsif (defined $m->[0]) {
        if (defined $m->[1]) {
            output $prefix<<(32-$bits), $bits, $indent unless defined $target;
            walk($prefix*2,   $bits+1, $indent+1, $m->[0]);
            walk($prefix*2+1, $bits+1, $indent+1, $m->[1]);
        } else {
            walk($prefix*2,   $bits+1, $indent, $m->[0]);
        }
    } else {
        if (defined $m->[1]) {
            walk($prefix*2+1, $bits+1, $indent, $m->[1]);
        } else {
            warn sprintf('Empty node at prefix=%x bits=%d indent=%d', $prefix, $bits, $indent);
        }
    }
}

walk (0, 0, 0, $map);
```

To execute in the syntax form.

```
$ chmod +x list2cidr.pl

$ ./list2cidr.pl <CIDR> ips.txt
```

### Bash

```bash
#!/bin/sh

xargs -I {} ipcalc -b {}/"$mask" < $1 |
awk -F ':' '$1 ~ /^Network/ && !seen[$2]++ { gsub(" ","",$2); print $2 }'
```

To execute in the syntax form.

```
$ chmod +x list2cidr.sh

$ ./list2cidr.sh <CIDR> ips.txt
```

---
## References

- [[Linux Commands References]]

- [Regex Find IP Addresses File Grep](https://www.shellhacks.com/regex-find-ip-addresses-file-grep/)

- [Convert List of IP Into Fixed CIDR Form](https://unix.stackexchange.com/questions/671839/convert-list-of-ip-into-fixed-cidr-form)
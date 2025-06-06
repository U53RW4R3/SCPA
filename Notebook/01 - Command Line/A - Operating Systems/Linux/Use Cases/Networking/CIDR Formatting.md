---
author(s):
  - Userware
tags:
  - command-line
  - networking
  - use-cases
  - linux
---
# CIDR Formatting

## Perl

```perl
#!/usr/bin/perl -w

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

## Bash

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

### StackExchange

- [StackExchange: Convert List of IP Into Fixed CIDR Form](https://unix.stackexchange.com/questions/671839/convert-list-of-ip-into-fixed-cidr-form)
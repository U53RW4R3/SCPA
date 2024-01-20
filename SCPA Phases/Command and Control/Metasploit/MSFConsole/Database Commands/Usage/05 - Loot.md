# 05 - Loot

Search Tag(s): #metasploit-framework #command-and-control

## 5.1 - Help Menu

```
msf > loot -h
Usage: loot [options]
 Info: loot [-h] [addr1 addr2 ...] [-t <type1,type2>]
  Add: loot -f [fname] -i [info] -a [addr1 addr2 ...] -t [type]
  Del: loot -d [addr1 addr2 ...]


OPTIONS:

    -a, --add                 Add loot to the list of addresses, instead of listing.
    -d, --delete              Delete *all* loot matching host and type.
    -f, --file <filename>     File with contents of the loot to add.
    -h, --help                Show this help information.
    -i, --info <info>         Info of the loot to add.
    -S, --search <filter>     Search string to filter by.
    -t, --type <type1,type2>  Search for a list of types.
    -u, --update              Update loot. Not officially supported.
```

## 5.2 - Usage

```
msf > loot

Loot
====

host       service  type            name               content     info            path
----       -------  ----            ----               -------     ----            ----
10.0.2.15           windows.hashes  DEFALT_hashes.txt  text/plain  Windows Hashes  /root/.msf4/loot/20220514174809_default_10.0.2.15_windows.hashes_764891.txt
```
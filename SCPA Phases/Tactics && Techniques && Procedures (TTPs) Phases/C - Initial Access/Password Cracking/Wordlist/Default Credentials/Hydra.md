# Hydra

## 01 - Help Menu

```
$ dpl4hydra help
dpl4hydra v0.9.9 (c) 2012 by Roland Kessler (@rokessler)

Syntax: dpl4hydra [help] | [refresh] | [BRAND] | [all]

This script depends on a local (d)efault (p)assword (l)ist called
/home/userware/.dpl4hydra/dpl4hydra_full.csv. If it is not available, regenerate it with
'dpl4hydra refresh'. Source of the default password list is
http://open-sez.me

Options:
  help        Help: Show this message
  refresh     Refresh list: Download the full (d)efault (p)assword (l)ist
              and generate a new local /home/grayfox/.dpl4hydra/dpl4hydra_full.csv file. Takes time!
  BRAND       Generates a (d)efault (p)assword (l)ist from the local file
              /home/userware/.dpl4hydra/dpl4hydra_full.csv, limiting the output to BRAND systems, using
              the format username:password (as required by THC hydra).
              The output file is called dpl4hydra_BRAND.lst.
  all         Dump list of all systems credentials into dpl4hydra_all.lst.

Example:
$ dpl4hydra linksys
File dpl4hydra_linksys.lst was created with 20 entries.
$ hydra -C ./dpl4hydra_linksys.lst -t 1 192.168.1.1 http-get /index.asp
```

## 02 - Usage

TODO: Fill this info

- Fetch the full default password list

```
$ dpl4hydra refresh
Trying to locate wget or curl... done.
Using curl for downloading data.

Trying to download list of vendors from
http://open-sez.me... done.


Merging download with /usr/share/hydra/dpl4hydra_local.csv... done.
Cleaning up and sorting /home/grayfox/.dpl4hydra/dpl4hydra_full.csv... done.

Refreshed (d)efault (p)assword (l)ist /home/grayfox/.dpl4hydra/dpl4hydra_full.csv
was created with 11079 entries.
```

- Limit the password with a brand name.

```
$ dpl4hydra <brand_name>

$ ls -l .dpl4hydra
```

---
## References

- [Open Sez Me!](https://open-sez.me/index.html)
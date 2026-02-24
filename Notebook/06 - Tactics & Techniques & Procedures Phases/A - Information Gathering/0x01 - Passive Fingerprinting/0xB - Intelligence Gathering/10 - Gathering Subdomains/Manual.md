---
author(s):
  - Userware
tags:
  - information-gathering
  - passive-fingerprinting
---
# Manual

## Extract Subdomains

```
$ grep -Eo "^([a-zA-Z0-9](([a-zA-Z0-9-]){0,61}[a-zA-Z0-9])?\.)+[a-zA-Z]{2,}$" file.txt | sort -uo subdomains.txt

$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' file.txt | sort -uo subdomains.txt
```

## Strip URI

```
$ grep -Po '^(.*://[^/]+)/' file.txt
```
---
author(s):
  - Userware
tags:
  - command-line
  - networking
  - regex
  - use-cases
  - linux
---
# Domains

## Extract Subdomains

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' file.txt | sort -u > subdomains-output.txt
```

## Strip URI

```
$ grep -Po '^(.*://[^/]+)/' file.txt
```
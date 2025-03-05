---
author(s):
  - Userware
tags:
  - command-line
  - use-cases
  - credential-stuffing
  - linux
---
# Credential Combolist

Combine usernames and passwords.

```
$ paste -d ":" users.lst passwords.list > combolist.lst

$ awk 'NR==FNR {a[FNR]=$1; next} {print a[FNR] ":" $1; }' users.lst passwords.lst > combolist.lst
```

Combine usernames and NTLM hashes.

```
$ paste -d ":" users.lst hashes.list > combolist.lst

$ awk 'NR==FNR {a[FNR]=$1; next} {print a[FNR] ":" $1; }' users.lst hashes.lst > combolist.lst
```
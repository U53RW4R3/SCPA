---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 02 - File and Directory Manipulation

## 2.1 - Touch

### 2.1.1 - Create an empty file

```
$ touch file.txt
```

## 2.2 -  File and Directory Permissions

TODO: Fill this info with table reference

```
$ chmod <[i]iii> file.txt
```


For SSH files.

| Element                 | File Type    | Permission         | Description                                                                             |
| ----------------------- | ------------ | ------------------ | --------------------------------------------------------------------------------------- |
| `$HOME/.ssh/`           | Directory    | 700 (`drwx------`) | SSH Directory                                                                           |
| `$HOME/id_rsa.pub`      | Regular File | 644 (`-rw-r--r--`) | Public keys                                                                             |
| `$HOME/id_rsa`          | Regular File | 600 (`-rw-------`) | Private keys                                                                            |
| `$HOME/authorized_keys` | Regular File | 600 (`-rw-------`) | File contains public keys that were copied and authorized to connect to the SSH server. |
| `$HOME/known_hosts`     | Regular File | 600 (`-rw-------`) | A list contains established SSH servers.                                                |
| `$HOME/config`          | Regular File | 600 (`-rw-------`) | A SSH config file.                                                                      |

## 2.3 -  File and Directory Ownership

```
$ chown <username>:<group> file.txt

$ chgrp <group> file.txt
```

---
## References

- [Linux Handbook: Fix Permission denied (publickey) SSH Error in Linux](https://linuxhandbook.com/fix-permission-denied-publickey/)
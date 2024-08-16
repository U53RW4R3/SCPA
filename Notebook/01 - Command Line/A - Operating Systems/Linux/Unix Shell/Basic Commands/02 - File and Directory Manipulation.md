# 02 - File and Directory Manipulation

Search Tag(s): #command-line #linux

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

## 2.4 -  File Attribution

To set the file immutable to make the file cannot be altered.

```
$ sudo chattr +i file.txt
```

Check the file permissions.

```
$ ls -lh file.txt
-rw-r--r-- 1 user user 22 Aug 13 18:11 file.txt
```

Removing the file even with elevated permissions won't be permitted.

```
$ sudo rm file.txt
rm: cannot remove 'file.txt': Operation not permitted
```

List the attributes from the file.

```
$ lsattr file.txt
----i---------e------- file.txt
```

To remove immutable attribute from the file. It can be altered.

```
$ sudo chattr -i file.txt
$ lsattr file.txt
--------------e------- file.txt
$ rm file.txt
```

---
## References

- [Wikipedia: Chattr](https://en.wikipedia.org/wiki/Chattr)

- [Linux Handbook: Fix Permission denied (publickey) SSH Error in Linux](https://linuxhandbook.com/fix-permission-denied-publickey/)

- [AtomicRedTeam: Defense Evasion T1222.002](https://atomicredteam.io/defense-evasion/T1222.002/)
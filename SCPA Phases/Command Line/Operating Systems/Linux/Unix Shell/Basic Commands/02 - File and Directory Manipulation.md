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

- [Chattr](https://en.wikipedia.org/wiki/Chattr)

- [AtomicRedTeam: Defense Evasion T1222.002](https://atomicredteam.io/defense-evasion/T1222.002/)
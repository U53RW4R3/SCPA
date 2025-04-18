---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 01 - Navigation and Exploration

## 1.1 - List Files and Directories

Print the current working directory.

```
$ pwd
```

List files and directories.

```
$ ls
```

Lists all the information from the files with permissions.

```
$ ls -l
```

List all files and folders including hidden ones and give the size of human readable bytes.

```
$ ls -lah
```

## 1.2 - Find

### 1.2.1 - Basics of find command

```
$ find / -type f -iname "*secrets*"

$ find / -type d -iname "config"

$ find / -type f -user <username>
```

### 1.2.2 - Find size of bytes

```
$ find / -type f -size 150
```

Find files that are less 10 Kilobytes with a file extension.

```
$ find / -type f -size -10k -name "*.txt"
```

### 1.2.3 - File ownership

Readable and writeable by the owner, and readable by everyone else (use octal format).

```
$ find / -type f -perm 644
```

Readable by anyone (octal format).

```
$ find / -type f -perm /444
```

Write permission for the group "others" with file extension.

```
$ find / -type f -perm o=w -name "*.sh"
```

Owned by root and have at least the SUID permission in `/usr/bin/` directory.

```
$ find /usr/bin -type f -user root -perm -u=s
```

Find all files that haven't been accessed in the last 10 days with file extension of "`*.png`."

```
$ find / -type f -atime +10 -name "*.png"
```

Find files that have been modified with the last 2 hours (120 minutes).

```
$ find /usr/bin -type f -mmin -120
```

# 1.3 - Change Directories

Specify path to change directory.

```
$ cd /path/to/directory/
```

Shift one level above the current directory.

```
$ cd ../
```

Change to the previous directory.

```
$ cd -
```

Return to home user directory (`/home/$USER`).

```
$ cd

$ cd ~

$ cd /home/$USER/
```
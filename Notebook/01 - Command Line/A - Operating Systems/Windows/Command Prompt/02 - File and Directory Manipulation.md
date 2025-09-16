---
author(s):
  - Userware
tags:
  - command-line
  - windows
---
# 02 - File and Directory Manipulation

## 2.1 - Create Files and Directories

### 2.1.1 - Create an empty file

```
C:\> con file.txt

C:\> copy NUL file.txt
```

### 2.1.2 - Create a directory

```
C:\> mkdir new_directory

C:\> md new_directory
```

### 2.1.3 - Delete directory

```
C:\> rd folder

C:\> rmdir folder
```

## 2.2 - File and Directory Attribution

TODO: Fill this info

Set the attributes by flagging it as hidden (`+h`), read only (`+r`), and important system file (`+s`)

```
C:\> attrib +h +r +s <file | directory>
```

Clear the attributes the by flagging them hidden (`-h`), read only (`-r`), and important system file (`-s`)

```
C:\> attrib -h -r -s <file | directory>
```
---
author(s):
  - Userware
tags:
  - command-line
  - windows
---
# 02 - File and Directory Manipulation

## 2.1 - Create an Empty File

```
PS C:\> New-Item -ItemType File -Name file.txt
```

## 2.2 - Create a Directory

```
PS C:\> New-Item -ItemType Directory -Name new_directory
```

## 2.3 - Delete a File

```
PS C:\> Remove-Item -Force -Recursive .\directory\
```

## 2.4 - Delete Folder

```
PS C:\> Remove-Item -Force -Recursive .\directory\
```
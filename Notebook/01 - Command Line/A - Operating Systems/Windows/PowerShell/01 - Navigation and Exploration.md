---
author(s):
  - Userware
tags:
  - command-line
  - windows
---
# 01 - Navigation and Exploration

## 1.1 - List Files and Directories

### 1.1.1 - List files

```
PS C:\> Get-ChildItem

PS C:\> Get-ChildItem | Format-Wide -Property Name -Column 1
```

## 2.1 - Change Directories

### 2.1.1 - Change directory

```
PS:\> Set-Location .\directory\
```
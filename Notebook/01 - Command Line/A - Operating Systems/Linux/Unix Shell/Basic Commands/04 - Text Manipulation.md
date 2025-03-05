---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 04 - Text Manipulation

## 4.1 - Remove ANSI Characters

```
$ sudo apt install -y ansifilter

$ ansifilter -i file.txt -o striped_ansi.txt
```
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
$ sed -e '\''s/\x1b\[[0-9;]*m//g'\'
```
---
author(s):
  - Userware
tags:
  - offensive-infrastructure
---
# Parse Python Packages

```
$ packages=$(awk -F "=" '{print "python3-"$1}' requirements.txt | tr "\n" " ")

$ sudo apt install -y $packages
```

Search for a specific package that causes conflict or software breakage.

```
$HOME/.local/lib/python3.*
/usr/local/lib/python3.*
```
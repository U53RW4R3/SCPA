---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-protocols
  - http
  - network-mapper
---
# Network Mapper

```
$ nmap -Pn -n -p 80,443 --script http-grep [--script-args http-grep.url="/path/to/url/"] <IP>
```
---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - ntp
---
# #network-mapper

TODO: Create headers to each commands.

```
$ sudo nmap -p 123 -sUV -Pn --script ntp-info,ntp-monlist <IP>
```

```
$ sudo nmap -p 123 -sUV --script "ntp-* and (discovery or vuln) and not (dos or brute)" <IP>
```
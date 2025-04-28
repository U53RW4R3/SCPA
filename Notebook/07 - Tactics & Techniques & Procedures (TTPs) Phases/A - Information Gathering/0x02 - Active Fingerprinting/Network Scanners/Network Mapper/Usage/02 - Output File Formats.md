---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 02 - Output File Formats

Normal output format.

```
$ sudo nmap -oN initial.nmap <IP>
```

Leet speak output format.

```
$ sudo nmap -oS initial.nmap <IP>
```

XML output format.

```
$ sudo nmap -oX initial.xml <IP>
```

Grepable output format.

```
$ sudo nmap -oG initial.gnmap <IP>
```

All output formats.

```
$ sudo nmap -oA initial <IP>
```
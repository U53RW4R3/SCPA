---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - whois
  - network-mapper
---
# WHOIS

## 01 - Manual

```
$ whois -h <IP> -p <PORT> "<website.com>"

$ echo "<website.com>" | nc -vn <IP> <PORT>
```

## 02 - Network Mapper

```
$ sudo nmap -p 43 -Pn -sCV <IP>
```
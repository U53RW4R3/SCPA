---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - whois
  - network-mapper
---
# WHOIS

## 01 - Manual

```
$ whois -H -h <IP> -p <PORT> "<domain.tld>"

$ echo "<domain.tld>" | nc -vn <IP> <PORT>
```

## 02 - Network Mapper

```
$ sudo nmap -p 43 -Pn -sCV <IP>
```
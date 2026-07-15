---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - netbios
  - network-mapper
---
# NETBIOS

## 01 - Name Resolution

```
$ nmap -p 137 -Pn -n <IP>
```

## 02 - Session Service

```
$ nmap -p 139 -Pn -n <IP>
```
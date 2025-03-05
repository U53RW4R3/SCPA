---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - upnp
  - network-mapper
---
# UPNP

## 01 - Network Mapper

```
$ sudo nmap -p 1900 -sU --script upnp-info <IP>

$ sudo nmap -sV --script broadcast-upnp-info <IP>
```
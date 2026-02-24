---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - upnp
  - network-mapper
---
# UPNP

## 01 - Network Mapper

```
$ sudo nmap -p 1900 -sU --script upnp-info <IP>

$ sudo nmap -sV --script broadcast-upnp-info <IP>
```
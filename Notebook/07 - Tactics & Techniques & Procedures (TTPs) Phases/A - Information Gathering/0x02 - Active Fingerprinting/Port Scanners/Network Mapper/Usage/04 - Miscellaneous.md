---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 04 - Miscellaneous

## 4.1 - Aggressive scan


> [!NOTE]
> This is an equivalent to these switches `nmap -O -sVC --traceroute <IP>`.

```
$ sudo nmap -A <IP>
```

List the network interfaces.

```
$ nmap --iflist
```
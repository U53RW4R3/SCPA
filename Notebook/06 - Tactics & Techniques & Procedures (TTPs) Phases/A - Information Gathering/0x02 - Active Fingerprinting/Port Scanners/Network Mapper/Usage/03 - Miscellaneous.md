---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 03 - Miscellaneous

## 3.1 - Aggressive scan

> [!INFO]
> This is an equivalent to these switches `nmap -O -sVC --traceroute <IP>`.

```
$ sudo nmap -A <IP>
```

List the network interfaces.

```
$ nmap --iflist
```
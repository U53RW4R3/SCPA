---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 01 - Port Specification and Scan Order

Specify port(s) to scan.

```
$ nmap -p <PORT>

$ nmap -p 25,53,80,443
```

Port range and list to scan

```
$ nmap -p 21-23 <IP>

$ nmap -p 21-23,25,53,80 <IP>
```

Scan all ports

```
$ nmap -p- <IP>
```

Show open ports

```
$ nmap --open <IP>
```

Print more information during a scan.

```
$ nmap -v <IP>
```

Increase more verbosity.

```
$ nmap -vv <IP>
```

---
## References

### Ethical hacking and penetration testing

- [Ethical hacking and penetration testing: Network Mapper usage tips](https://miloserdov.org/?p=3639)
---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 03 - Scan Techniques

## 3.1 - TCP

TCP Connect Scan

```
$ sudo nmap -sT <IP>
```

Syn "Half-open" Scan (Stealth Mode)

```
$ sudo nmap -sS <IP>
```

## 3.2 - UDP

UDP Scan

```
$ sudo nmap -sU <IP>
```

## 3.3 - Other Scan Types

TCP Null Scan

```
$ sudo nmap -sN <IP>
```

FIN Scan

```
$ sudo nmap -sF <IP>
```

Xmas Scan

```
$ sudo nmap -sX <IP>
```

ACK Scan

```
$ sudo nmap -sA <IP>
```

Window Scan

```
$ sudo nmap -sW <IP>
```

Maimon Scan

```
$ sudo nmap -sM <IP>
```

## 3.4 - Version Detection

Detect operating system

```
$ sudo nmap -O <IP>
```

Service Version detection
^07168f

```
$ sudo nmap -sV <IP>

$ sudo nmap -sV --version-all <IP>
```

## 3.5 - Firewall Detection

Best against towards stateful firewalls.

```
$ nmap -sn -n -PS <PORT> <IP>
```

Best against towards stateless firewalls.

```
$ nmap -sn -n -PA <PORT> <IP>
```

---
## References

### Ethical hacking and penetration testing

- [Ethical hacking and penetration testing: Network Mapper usage tips](https://miloserdov.org/?p=3639)
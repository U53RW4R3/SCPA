---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - command-and-control
  - detection
  - metasploit-framework
---
# Detection

## 01 - Shodan

```
ssl:"MetasploitSelfSignedCA"
```

## 02 - Censys

```
services.software.product=`Metasploit`
```

---
## References

### Censys

- [Censys: Russian Ransomware C2 Network Discovered in Censys Data](https://censys.com/russian-ransomware-c2-network-discovered-in-censys-data/)

### Michael Koczwara

- [Michael Koczwara: Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)
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

## 03 - JARM

```
$ git clone https://github.com/salesforce/jarm.git

$ cd jarm/

$ python jarm.py <C2_IP> -p 4444

$ python jarm.py <C2_IP> -p 443

$ python jarm.py <C2_IP> -p 80
```

---
## References

### Source Repositories

- [drb-ra: C2IntelFeeds](https://github.com/drb-ra/C2IntelFeeds)

- [cedowens: C2 JARM](https://github.com/cedowens/C2-JARM)

- [salesforce: JARM](https://github.com/salesforce/jarm)

### Censys

- [Censys: Russian Ransomware C2 Network Discovered in Censys Data](https://censys.com/russian-ransomware-c2-network-discovered-in-censys-data/)

### Michael Koczwara

- [Michael Koczwara: Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)
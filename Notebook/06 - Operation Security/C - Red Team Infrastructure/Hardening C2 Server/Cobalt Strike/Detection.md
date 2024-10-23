---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - cobalt-strike
  - detection
---
# Detection

## 01 - Shodan

```
product:"Cobalt Strike Beacon"
```

## 02 - JARM

```
$ git clone https://github.com/salesforce/jarm.git

$ cd jarm/

$ python jarm.py <C2_IP> -p 80

$ python jarm.py <C2_IP> -p 443
```

---
## References

### Github

- [drb-ra: C2IntelFeeds](https://github.com/drb-ra/C2IntelFeeds)

- [JARM](https://github.com/salesforce/jarm)

- [C2 JARM](https://github.com/cedowens/C2-JARM)

- [C2 Tracker](https://github.com/montysecurity/C2-Tracker)

- [JARM Randomizer](https://github.com/netskopeoss/jarm_randomizer)

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)

- [Spoofing JARM Signatures I Am The Cobalt Strike Server Now](https://grimminck.medium.com/spoofing-jarm-signatures-i-am-the-cobalt-strike-server-now-a27bd549fc6b)

- [JARM Randomizer Evading JARM Fingerprinting Dagmawi Mulugeta Presentation PDF File](https://conference.hitb.org/hitbsecconf2021ams/materials/D2%20COMMSEC%20-%20JARM%20Randomizer%20Evading%20JARM%20Fingerprinting%20-%20Dagmawi%20Mulugeta.pdf)
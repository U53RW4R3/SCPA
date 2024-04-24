# Detection

Search Tag(s): #red-team-infrastructure #metasploit-framework #detection

## 01 - Shodan

`ssl:"MetasploitSelfSignedCA"`

## 02 - Censys

```
services.software.product=`Metasploit`
```

## 03 - JARM

`$ git clone https://github.com/salesforce/jarm.git`

`$ cd jarm/`

`$ python jarm.py <C2_IP> -p 4444`

`$ python jarm.py <C2_IP> -p 443`

`$ python jarm.py <C2_IP> -p 80`

---
## References

- [drb-ra: C2IntelFeeds](https://github.com/drb-ra/C2IntelFeeds)

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)

- [C2 JARM](https://github.com/cedowens/C2-JARM)

- [Russian Ransomware C2 Network Discovered in Censys Data](https://censys.com/russian-ransomware-c2-network-discovered-in-censys-data/)

- [JARM](https://github.com/salesforce/jarm)
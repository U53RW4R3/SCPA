---
author(s):
  - Userware
tags:
  - information-gathering
  - passive-fingerprinting
  - network-protocols
  - network-mapper
---
# Network Mapper

```
$ nmap -sn -Pn -n --script shodan-api --script-args 'shodan-api.apikey=<API_KEY>,shodan-api.outfile=shodan-output.csv' <IP>/<CIDR>

$ nmap --script shodan-api --script-args 'shodan-api.apikey=<API_KEY>,shodan-api.target=<IP>,shodan-api.outfile=shodan-output.csv'
```

---
## References

- [Network Mapper NSEDoc: Shodan-API NSE Script](https://nmap.org/nsedoc/scripts/shodan-api.html)
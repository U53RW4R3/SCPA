---
author(s):
  - Userware
tags:
  - information-gathering
  - passive-fingerprinting
  - network-protocols
  - tls
  - network-mapper
---
# Network Mapper

```
$ nmap -p 443 -Pn --script ssl-date,ssl-cert-intaddr,ssl-enum-ciphers,sslv2 <IP>
```

Probe for subdomains

```
$ nmap -p 443 -Pn --script ssl-cert <IP>
```

^7c92b9
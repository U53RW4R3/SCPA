# Network Mapper

Search Tag(s): #information-gathering #passive-reconnaissance #network-protocols #network-mapper

```
$ nmap -p 443 -Pn --script ssl-date,ssl-cert-intaddr,ssl-enum-ciphers,sslv2 <IP>
```

Probe for subdomains

```
$ nmap -p 443 -Pn --script ssl-cert <IP>
```
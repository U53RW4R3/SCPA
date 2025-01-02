# Network Mapper

Search Tag(s): #information-gathering #passive-reconnaissance #network-protocols #network-mapper

```
$ nmap --script whois-domain <IP>
```

Gather network blocks, netname, organization name, organization ID, country, tech name, and tech email.

```
$ nmap --script whois-ip 

$ nmap --script whois-ip --script-args whois.whodb=nofile <IP>
```

Tech emails may vary when you change the arguments.

```
$ nmap --script whois-ip --script-args whodb=arin+ripe+afrinic <IP>

$ nmap --script whois-ip --script-args whois.whodb=apnic*lacnic

$ nmap --script whois-ip --script-args whodb=nofollow <IP>

$ nmap --script whois-ip --script-args whois.whodb=nofollow+ripe <IP>

$ nmap --script whois-ip --script-args whodb=nocache <IP>

$ nmap --script whois-ip --script-args whois.whodb=nocache <IP>
```

---
## References

- [Network Mapper NSEDoc: Script whois-ip](https://nmap.org/nsedoc/scripts/whois-ip.html)
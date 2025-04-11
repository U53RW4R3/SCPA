# Scanners

## 01 - Whatweb

```
$ whatweb -v <URL>
```

## 02 - Metasploit

TODO: Show the steps

```
msf > use auxiliary/scanner/http/http_header

msf auxiliary(scanner/http/http_header) > set rhosts <IP>

msf auxiliary(scanner/http/http_header) > set rport <PORT>

msf auxiliary(scanner/http/http_header) > run
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xD - Network Ports/HTTP/Webapp Information/Whatweb|Whatweb]]
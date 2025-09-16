# Scanners

## 01 - Whatweb

```
$ whatweb -p Proxy-Agent,Proxy-Authenticate <URL>
```

## 02 - Network Mapper

Discover open HTTP proxy.

```
$ nmap -p 80,443,3128,8000,8080,8443 -Pn -n --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>
```

## 03 - Metasploit

TODO: Show the steps

```
msf > use auxiliary/scanner/http/open_proxy
```

```
msf > use auxiliary/scanner/http/squid_pivot_scanning
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/0x03 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents]]

- [[ProxyTunnel]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Broken Access control/Server-Side Attack/Authorization Bypass/HTTP Error Code Bypass/Scanners/Network Mapper|Network Mapper: Authorization Bypass]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Broken Authentication/Bruteforce Login/HTTP Basic Authentication/Scanners|Network Mapper: HTTP Basic Authentication]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/0x02 - Components with Known Vulnerabilities/Helpers/Scanners|Network Mapper: Components with Known Vulnerabilities]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/0x05 - Sensitive Data Exposure/Web Content Discovery/Helpers/Scanners|Network Mapper: Web Applications Forensics]]

### Hacktricks

- [Hacktricks: Pentesting Squid](https://book.hacktricks.wiki/en/network-services-pentesting/3128-pentesting-squid.html)
# Nmap

Discover open HTTP proxy.


```
$ nmap -p 80,443,3128,8000,8080,8443 -Pn -n --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Broken Access control/Authorization Bypass/Scanners/Nmap|Nmap: Authorization Bypass]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Broken Authentication/Bruteforce Login/HTTP Basic Authentication/Scanners/Nmap|Nmap: HTTP Basic Authentication]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Components with Known Vulnerabilities/Scanners/Nmap|Nmap: Components with Known Vulnerabilities]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Sensitive Data Exposure/Web Applications Forensics/Scanners/Nmap|Nmap: Web Applications Forensics]]

- [[User Agents]]

- [[ProxyTunnel]]
# Scanners

## 01 - Nmap

Discover open HTTP proxy.

```
$ nmap -p 80,443,3128,8000,8080,8443 -Pn -n --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>
```

## 02 - Metasploit

```
msf > use auxiliary/scanner/http/open_proxy
```

```
msf > use auxiliary/scanner/http/squid_pivot_scanning
```

---
## References

- [[User Agents]]

- [[ProxyTunnel]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Broken Access control/Server-Side Attack/Authorization Bypass/Scanners/Nmap|Nmap: Authorization Bypass]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Broken Authentication/Bruteforce Login/HTTP Basic Authentication/Scanners/Nmap|Nmap: HTTP Basic Authentication]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Components with Known Vulnerabilities/Scanners/Nmap|Nmap: Components with Known Vulnerabilities]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/Sensitive Data Exposure/Web Applications Forensics/Scanners/Nmap|Nmap: Web Applications Forensics]]

- [Hacktricks: Pentesting Squid](https://book.hacktricks.xyz/network-services-pentesting/3128-pentesting-squid)
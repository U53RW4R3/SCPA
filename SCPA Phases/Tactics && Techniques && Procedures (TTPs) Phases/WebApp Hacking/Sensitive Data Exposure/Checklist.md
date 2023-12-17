# Checklist

TODO: Provide a checklist for Sensitive Data Exposure

## Information Gathering

### Active Reconnaissance

#### Active Enumeration

##### Discover Ports

- [ ] Probing ports to check what service version of the webservers using [[06 - Scan Techniques|nmap]].

##### Webserver Enumeration

- [ ] Check the [[Sensitive File List|common sensitive file list]] to find sensitive files.
- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Network Protocols/HTTP/09 - HTTP Enumeration/Nmap|NSE script]] to enumerate the webservers with `-iL ips.txt` flag.
- [ ] Perform directory bruteforce via [[Gobuster]].

## Vulnerability Assessment

### Scanners

#### General

- [ ] Use [[Wapiti]] to find potential exploits.
- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/Vulnerability Assessment/Web Vulnerability Scanner/Nikto|Nikto]] scanner to discover for existing vulnerabilities.
- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Sensitive Data Exposure/Web Applications Forensics/Scanners/Nmap|NSE script]] to probe for information disclosure and vulnerabilities on the webservers with `-iL ips.txt` flag.
- [ ] Using [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Sensitive Data Exposure/Web Applications Forensics/Scanners/Nuclei|Nuclei]] with a default templates to discover configuration files exposed on the webservers.
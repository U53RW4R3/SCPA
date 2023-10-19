# Checklist

TODO: Provide a checklist for Sensitive Data Exposure

## Information Gathering

### Active Reconnaissance

#### Active Enumeration

##### Discover Ports

- [ ] Probing ports to check what service version of the webservers using [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Active Fingerprinting/Port Scanners/Nmap#^07168f|nmap]].

##### Webserver Enumeration

- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Active Fingerprinting/Enumeration/Network Protocols/HTTP/Tools/Nmap|NSE script]] to enumerate the webservers with `-iL ips.txt` flag.
- [ ] Perform directory bruteforce via [[Gobuster]].
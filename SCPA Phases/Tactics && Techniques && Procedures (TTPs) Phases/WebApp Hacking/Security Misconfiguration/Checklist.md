# Checklist

TODO: Provide a checklist for security misconfiguration

## Default Credentials

- [ ] Router default credentials
- [ ] Web panel default credentials

### Vulnerability Assessment

- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Security Misconfiguration/Default Credentials/Scanners/Nmap|NSE script]] to perform bruteforce the default crednetials on the webservers and IoTs with `-iL ips.txt` flag.

## API

### Information Gathering

#### Enumeration

- [ ] Check the [[Sensitive File List|common sensitive file list]] to find APIs.
- [ ] Fuzz existing [[API Endpoint Wordlist|API endpoint]] directories.
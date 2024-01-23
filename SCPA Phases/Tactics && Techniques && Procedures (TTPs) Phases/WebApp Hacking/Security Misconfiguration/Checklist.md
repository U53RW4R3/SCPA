# Checklist

TODO: Provide a checklist for security misconfiguration

## Default Credentials

- [ ] Router default credentials
- [ ] Web panel default credentials

### Vulnerability Assessment

- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Security Misconfiguration/Default Credentials/Scanners/Nmap|NSE script]] to perform bruteforce the default credentials on the webservers and IoTs with `-iL ip_targets.txt` flag.
- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Security Misconfiguration/Default Credentials/Scanners/Nikto|nikto]] scanner to perform bruteforce for default credentials on the webservers.

## API

### Information Gathering

#### Enumeration

- [ ] Check the [[Sensitive File List|common sensitive file list]] to find APIs.
- [ ] Fuzz existing [[API Endpoint Wordlist|API endpoint]] directories.
# Checklist

Search Tag(s): #checklist #command-injection #shellshock 

TODO: Fill this info

## Information Gathering

### Active Enumeration

- [ ] Probing ports to check what service version of the webservers.
- [ ] Find common directories with a list of [[Shellshock List|Common Gateway Interface (CGI)]] or perform [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Web Crawlers and Directory Bruteforce/Metasploit|web crawling or directory bruteforce]].
- [ ] Perform [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Web Crawlers and Directory Bruteforce/Metasploit|directory bruteforce]] after checking CGIs directories on the webserver to find specific file extensions: `.sh`

## Vulnerability Assessment

### Scanners

#### General

- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/Vulnerability Assessment/Web Vulnerability Scanner/Nikto|Nikto]] scanner to discover for existing shellshock exploits.
- [ ] Use [[Wapiti]] to find potential shellshock exploits.
- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Command Injection/Scanners/Nmap|NSE script]] to probe for shellshock vulnerabilities on the webservers with `-iL ips.txt`.

## Exploit

- [ ] Run with [[Commix]] using the `--shellshock` module to test for command injections.
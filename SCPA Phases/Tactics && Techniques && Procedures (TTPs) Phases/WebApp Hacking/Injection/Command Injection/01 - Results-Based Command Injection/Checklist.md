# Checklist

Search Tag(s): #checklist #command-injection

TODO: Provide a checklist for command injection

## DBMS

- [ ] GraphQL

## Information Gathering

### Passive Reconnaissance

#### IoTs

- [ ] Routers
- [ ] Printers
- [ ] CCTV Cameras
- [ ] IP PBX Applications or VoIP

#### Discover Hidden Parameters

- [ ] Find common parameters to perform command injection via [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/Command Injection/Manual|google dorks]].
- [ ] Spider the webservers with [[Katana|katana]] or [[Gospider|gospider]] to find hidden parameters.
- [ ] Browse the website with OWASP ZAP or Burp Suite to see any potential interest.

### Active Reconnaissance

#### Active Enumeration

##### Discover Ports

- [ ] Probing ports to check what service version of the webservers using [[06 - Scan Techniques|nmap]].

##### Fuzz Hidden Parameters

TODO: I got this covered - Userware

- [ ] To bruteforce hidden parameters use [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Fuzzers/Bruteforce Parameters/FFuF|Fuff]] or [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Fuzzers/Bruteforce Parameters/Wfuzz|Wfuzz]].
- [ ] [[Arjun]] and [[x8]] and [[WaybackURLs]] and [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/Enumeration/HTTP/Wayback Machine/Metasploit|Metasploit]].

## Vulnerability Assessment

### Scanners

#### General

- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Command Injection/Scanners/Nikto|nikto]] scanner to discover for existing command injection exploits.
- [ ] Look for shellshock vulnerabilities in the [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Command Injection/03 - Shellshock/Checklist|shellshock checklist]].

#### Content Management System

- [ ] Run [[WPScan]] to check for vulnerable wordpress plugins or themes related to command injection.
- [ ] Run [[Joomscan]] to check for vulnerable joomla plugins or themes related to command injection.

## Exploit

### Manual Injection on Parameters

#### Common Parameters

- [ ] Check the top parameters in [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/SQL Injection/Manual|google dorks]].
- [ ] Whois Lookup
- [ ] DNS Lookup
- [ ] Ping
- [ ] Traceroute

#### GET Request

- [ ] Check the URL parameters

#### POST Request

- [ ] Check POST JSON parameters
- [ ] POST parameters may contain in SOAP/XML

### Manual Injection on Headers

- [ ] Inject commands in **X-Forwarded-For**
- [ ] Inject commands in **X-Forwarded-Host**
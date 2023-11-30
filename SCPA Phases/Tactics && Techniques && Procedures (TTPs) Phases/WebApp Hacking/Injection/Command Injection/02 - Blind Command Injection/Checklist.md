# Checklist

Search Tag(s): #checklist #command-injection

TODO: Provide a checklist for blind command injection

## DBMS

- [ ] GraphQL

## IoTs

- [ ] Routers
- [ ] Printers
- [ ] CCTV Cameras
- [ ] IP PBX Applications or VoIP

## Information Gathering

### Passive Reconnaissance

#### IoTs

- [ ] Routers
- [ ] Printers
- [ ] CCTV Cameras
- [ ] IP PBX Applications or VoIP

#### Discover Hidden Parameters

- [ ] Find common parameters to perform blind command injection via [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/Command Injection/Manual|google dorks]].
- [ ] Spider the webservers with [[Katana|katana]] or [[Gospider|gospider]] to find hidden parameters.

### Active Reconnaissance

#### Active Enumeration

##### Discover Ports

- [ ] Probing ports to check what service version of the webservers using [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Active Fingerprinting/Port Scanners/Nmap#^07168f|nmap]].

##### Fuzz Hidden Parameters

TODO: I got this covered - Userware

- [ ] To bruteforce hidden parameters use [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Active Fingerprinting/Enumeration/Fuzzers/Bruteforce Parameters/FFuF|Fuff]] or [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Active Fingerprinting/Enumeration/Fuzzers/Bruteforce Parameters/Wfuzz|Wfuzz]].
- [ ] [[Arjun]] and [[x8]] and [[WaybackURLs]].

## Vulnerability Assessment

### Scanners

#### General

- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/Vulnerability Assessment/Web Vulnerability Scanner/Nikto]] scanner to discover for existing blind command injection exploits.

#### Content Management System

- [ ] Run [[WPScan]] to check for vulnerable wordpress plugins or themes related to blind command injection.
- [ ] Run [[Joomscan]] to check for vulnerable joomla plugins or themes related to blind command injection.

## Exploit

### Manual Injection on Parameters

#### Common Parameters

- [ ] Check the top parameters in [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/SQL Injection/Manual|google dorks]].
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

- [ ] Inject commands in X-Forwarded-For
- [ ] Inject commands in X-Forwarded-Host
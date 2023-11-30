# Checklist

Search Tag(s): #checklist #path-traversal #webapp

## Information Gathering

### Passive Reconnaissance

#### Discover Hidden Parameters

- [ ] Find common parameters to perform path traversal via [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/Path Traversal/Manual|google dorks]].
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

- [ ] Use [[Wapiti]] to find potential path traversal exploits.
- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/Vulnerability Assessment/Web Vulnerability Scanner/Nikto]] scanner to discover for existing path traversal exploits.
- [ ] Using [[Nuclei]] with fuzzer templates to discover GET request URLs with path traversal vulnerabilities.

#### Content Management System

- [ ] Run [[WPScan]] to check for vulnerable wordpress plugins or themes related to path traversal.
- [ ] Run [[Joomscan]] to check for vulnerable joomla plugins or themes related to path traversal.

## Exploit

### Manual Injection on Parameters

#### Common Parameters

- [ ] Check the top parameters in [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/Path Traversal/Manual|google dorks]].

#### GET Request

- [ ] Check the URL parameters

#### POST Request

- [ ] Perform username enumeration to craft the SQL injection
- [ ] Check POST JSON parameters
- [ ] POST parameters may contain in SOAP/XML

### Manual Injection on Headers

- [ ] Inject X-Forwarded-For
- [ ] Inject X-Forwarded-Host
- [ ] Inject User-Agent header

### Initial Foothold

#### Evasion

- [ ] Use PHP filewrapper to bypass filter

#### Remote File Inclusion (RFI)

- [ ] Find a file upload form to navigate and execute it with directory traversal
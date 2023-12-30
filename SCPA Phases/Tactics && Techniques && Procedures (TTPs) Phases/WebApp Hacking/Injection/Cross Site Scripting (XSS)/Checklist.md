# Checklist

Search Tag(s): #checklist #xss #webapp

TODO: Provide more checklists for XSS

## Information Gathering

### Passive Reconnaissance

#### Discover Hidden Parameters

- [ ] Find common parameters to perform XSS exploits via [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/Cross-Site Scripting/Manual|google dorks]].
- [ ] Spider the webservers with [[Katana|katana]] or [[Gospider|gospider]] to find hidden parameters.
- [ ] Browse the website with OWASP ZAP or Burp Suite to see any potential interest.

### Active Reconnaissance

#### Active Enumeration

##### Discover Ports

- [ ] Probing ports to check what service version of the webservers using [[06 - Scan Techniques|nmap]].

##### Fuzz Hidden Parameters

TODO: I got this covered - Userware

- [ ] To bruteforce hidden parameters use [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Fuzzers/Bruteforce Parameters/FFuF|FFuF]] or [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Fuzzers/Bruteforce Parameters/Wfuzz|Wfuzz]].
- [ ] [[Arjun]] and [[x8]] and [[WaybackURLs]] and [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/Enumeration/HTTP/Wayback Machine/Metasploit|Metasploit]].

## Vulnerability Assessment

### Scanners

#### General

- [ ] Use [[Wapiti]] to find potential XSS exploits.
- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Cross Site Scripting (XSS)/Scanners/Nikto|nikto]] scanner to discover for existing XSS exploits.
- [ ] You can use XSS scanners to perform and inject Cross-Site Scripting (XSS) payloads for heuristic checks.
	- [[Dalfox]]
	- [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Cross Site Scripting (XSS)/Scanners/XSSer|XSSer]]
	- [[XSStrike]]
- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Cross Site Scripting (XSS)/Scanners/Nmap|NSE script]] to probe for XSS vulnerabilities on the webservers with `-iL ips.txt` flag.
- [ ] Using [[Webapps|Nuclei]] with fuzzer templates to discover GET request URLs with XSS vulnerabilities.

#### Content Management System

- [ ] Run [[WPScan]] to check for vulnerable wordpress plugins or themes related to XSS exploits.
- [ ] Run [[Joomscan]] to check for vulnerable joomla plugins or themes related to XSS exploits.

## Exploit

### Manual Injection on Parameters

#### GET Request

- [ ] Check the URL parameters.
- [ ] Check the URI parameters.

#### POST Request

- [ ] Check contact form to insert payload before submitting a message
- [ ] In a email form insert like this `"><script>alert(1)</script>"@email.com`

### Manual Injection on Headers

- [ ] Inject Cookie headers
- [ ] Inject User-Agent
- [ ] Inject X-Forwarded-For
- [ ] Inject X-Forwarded-Host

### Exploit Chaining

#### Stored XSS

- [ ] Waterfall

#### File Upload

- Include metadata with `exiftool` with any of these tags:
	- [ ] Comment
	- [ ] Copyright
	- [ ] DocumentName
- [ ] Include XSS payload in the basename of the file. For example: `"><script>alert(1)</script>.png`
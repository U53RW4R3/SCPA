# Checklist

Search Tag(s): #checklist #blind-sql-injection #webapp

TODO: Fill the rest of checklist for Blind SQL injection

## Information Gathering

### Passive Reconnaissance

#### Discover Hidden Parameters

- [ ] Find common parameters to perform blind SQL injection via [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/SQL Injection/Manual|google dorks]].
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

- [ ] Use [[Wapiti]] to find potential blind SQL injection exploits.
- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/SQL Injection/Scanners/Nikto|nikto]] scanner to discover for existing blind SQL injection exploits.
- [ ] You can use XSS scanners to perform and inject Cross-Site Scripting (XSS) payloads for heuristic checks as a probable indicator for blind SQL injection exploits.
	- [[Dalfox]]
	- [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Cross Site Scripting (XSS)/Scanners/XSSer|XSSer]]
	- [[XSStrike]]
- [ ] Run an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/SQL Injection/Scanners/Nmap|NSE script]] to probe for blind SQL injection vulnerabilities on the webservers with `-iL ips.txt` flag.
- [ ] Using [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/SQL Injection/Scanners/Nuclei|Nuclei]] with fuzzer templates to discover GET request URLs with blind SQL injection vulnerabilities and other indicators of PHP syntax code disclosure.
- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/SQL Injection/Scanners/Metasploit|metasploit]] auxiliary scanner module to find blind SQL injection vulnerabilities on the webservers.

#### Content Management System

- [ ] Run [[WPScan]] to check for vulnerable wordpress plugins or themes related to blind SQL injection.
- [ ] Run [[Joomscan]] to check for vulnerable joomla plugins or themes related to blind SQL injection.

## Exploit

### Manual Injection on Parameters

- Refer to [[Inferential SQL Queries]] to aid to exploit the vulnerability.

#### Common Parameters

- [ ] Check the top parameters in [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/01 - Passive Fingerprinting/OSINT/Search Engines Dorking/Google Dorking/Dorks/Web Enumeration/SQL Injection/Manual|google dorks]].

#### GET Request

- [ ] Check the URL parameters.
- [ ] Check the URI parameters.
- [ ] Perform on numeric parameters with mathematical expression as a probable indicator for blind SQL injection. In **SQLMap** this can be possible with `--invalid-bignum` flag.

```
--invalid-logical   Use logical operations for invalidating values
--invalid-string    Use random strings for invalidating values
```

#### POST Request

- [ ] Perform username enumeration to craft the SQL injection
- [ ] Check JSON parameters
- [ ] POST parameters may contain in SOAP/XML

### Manual Injection on Headers

- [ ] Inject **X-Forwarded-For**
- [ ] Inject **X-Forwarded-Host**
- [ ] Inject Cross-Site Scripting (XSS) payloads as a probable indicator of blind SQL injection.

### Blind SQL Injection Responses

#### Page Comparison

TODO: Fill out the page comparison for blind SQL injection

##### Boolean-Based Blind SQL Injection

- Compare responses of what conditions are needed:
	- [ ] Trigger valid response of what input accepts.
	- [ ] Trigger invalid response of what input returns an error.
	- [ ] Conditional error response.
	- [ ] Observe title webpage response.
	- [ ] Observe HTTP status code.

##### Time-Based Blind SQL Injection



### Data Collection

#### Login Panels

- [ ] Perform Boolean-based SQL injection to bypass authentication. In **SQLMap** you can specify `--technique=B` flag which allows you to dump the database credentials. Whatever based on your enumeration gathering based on the webapp response include these flags to narrow it down:
	-  `--string` for single response or `--regexp` multiple responses if returned true. `--code=200` if HTTP code status is true or `--code=401` if HTTP code status is false.
	- `--not-string` for single response if returned false.
	- To perform another check to highest success rate of SQL injection exploit add `--titles` flag to compare the webpages based on title response.
	- if possible you can use another inferential SQL injection techniques: 
		- [ ] Time-based blind query (`--technique=T`). To narrow it down:
			- `--time-sec` to increase the sleep delay response
- [ ] Find an login (admin) panel to login the credentials you've obtained from the current database. Use [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Web Crawlers and Directory Bruteforce/Gobuster|gobuster]] if you must.

#### DBMS Credentials

- [ ] After you successfully exploited the parameters. Extract the DBMS credentials to authenticate the database server. You can perform this in [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/SQL Injection/03 - Automated Exploitation/SQLMap/Scenarios/Discovery and Enumeration/Database/05 - Credentials|SQLMap]].
- [ ] Run a port scanner like [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/Active Fingerprinting/Port Scanners/Nmap/Usage/Nmap|Nmap]] or [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Port Scanners/Naabu|Naabu]] to discover DBMS open ports.

### Initial Foothold

#### Webshell

TODO: Write more about this

##### Enumerate Web Root Directory

- Discover and enumerate the web root directory.
	- [ ] Find syntax errors or warning messages to find a web root directory.
	- [ ] A directory path where to upload files.

##### Upload File

- [ ] After successfully exploiting blind SQL injection. Upload a webshell if possible.

### Exploit Chaining

- [ ] If **SQLMap** detects the blind SQL injection parameters with positive heuristic checks of XSS. Craft an [[Tactics && Techniques && Procedures (TTPs) Phases/WebApp Hacking/Injection/Cross Site Scripting (XSS)/Lab Simulation/01 - DVWA/Stored XSS/Difficulty/Low/Manual#^a7f343|XSS payload]] then insert it in the database to steal cookie sessions.
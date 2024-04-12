# Checklist

TODO: Provide the checklist for public webapp exploits

## Information Gathering

### Passive Reconnaissance

#### IoTs

- [ ] Routers
- [ ] Printers
- [ ] CCTV Cameras
- [ ] IP PBX Applications or VoIP

### Active Reconnaissance

#### Active Enumeration

##### Discover Ports

- [ ] Probing ports to check what service version using [[06 - Scan Techniques|nmap]].

## Vulnerability Assessment

### Scanners

#### General

- [ ] Run [[Tactics && Techniques && Procedures (TTPs) Phases/B - Vulnerability Assessment/Scanners/Web Vulnerability Scanner/Nikto|Nikto]] scanner to discover for existing webapp exploits.
- [ ] Use [[Tactics && Techniques && Procedures (TTPs) Phases/D - WebApp Hacking/Components with Known Vulnerabilities/Scanners/Nuclei|nuclei]] with a default templates to discover vulnerable webapp components.
- [ ] Look for shellshock vulnerabilities in the [[Tactics && Techniques && Procedures (TTPs) Phases/D - WebApp Hacking/Injection/Command Injection/03 - Shellshock/Checklist|shellshock checklist]].

#### Content Management System

- [ ] Run [[WPScan]] to check for vulnerable wordpress plugins or themes.
- [ ] Run [[Joomscan]] to check for vulnerable joomla plugins or themes.

#### IoTs

- [ ] [[Tactics && Techniques && Procedures (TTPs) Phases/C - Initial Access/Internet of Things (IoT)/Routers/Routers#^7d9f1e|Routersploit]] via `autopwn/scanner` module

### Exploits

- [ ] [[ExploitDB]]
- [ ] [[Pompem]]
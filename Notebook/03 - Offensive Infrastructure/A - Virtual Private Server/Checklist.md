---
author(s):
  - Userware
tags:
  - checklist
  - red-team-infrastructure
---
# Checklist

TODO: Provide a checklist when setting up to every c2 framework

## Reputation

### IP Address and Domain

- [ ] Check the VPS's IP address if it's been abused before.
- [ ] Check the domain.
- [ ] Check the **Autonomous System (AS)** number is blocked within the range.
- Use these services to check:
	- [AbuseIPDB](https://www.abuseipdb.com)
	- [MS Lookup Tool: Blacklists](https://mxtoolbox.com/blacklists.aspx)

## Setup Infrastructure

- [ ] Overlap with legit domains.
- [ ] Register expired domains.
- [ ] Ensure the domain isn't registered less than a month.
- [ ] Register the domain without any WHOIS partial exposure.

## Diagnostics

### HTTP(S)

- [ ] Verify the redirector or domain fronting is working by hosting a text file. 

---
## References

### Cobalt Strike

- [Cobalt Strike User Guide: Valid SSL Certificates with SSL Beacon](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_valid-ssl-certificates.htm)
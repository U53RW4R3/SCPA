# Recon-ng

- `viewdns_reverse_whois` recon-ng module

```
[recon-ng][default] > marketplace install recon/companies-domains/viewdns_reverse_whois

[recon-ng][default] > modules load recon/companies-domains/viewdns_reverse_whois

[recon-ng][default][viewdns_reverse_whois] > options set SOURCE <domain.com>

[recon-ng][default][viewdns_reverse_whois] > options set SOURCE query SELECT DISTINCT host FROM hosts WHERE host IS NOT NULL

[recon-ng][default][viewdns_reverse_whois] > run

[recon-ng][default][viewdns_reverse_whois] > back
```

- `whois_miner` recon-ng module

```
[recon-ng][default] > marketplace install recon/companies-multi/whois_miner

[recon-ng][default] > modules load recon/companies-multi/whois_miner

[recon-ng][default][whois_miner] > options set SOURCE <domain.com>

[recon-ng][default][whois_miner] > run

[recon-ng][default][whois_miner] > back
```

- `whois_orgs` recon-ng module

```
[recon-ng][default] > marketplace install recon/netblocks-companies/whois_orgs

[recon-ng][default] > modules load recon/netblocks-companies/whois_orgs

[recon-ng][default][whois_orgs] > options set SOURCE <domain.com>

[recon-ng][default][whois_orgs] > run

[recon-ng][default][whois_orgs] > back
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Enumeration/DNS/01 - Gather Subdomains/Scanners/Recon-ng|DNS Enumeration: Recon-ng]]

- [ViewDNS.info](https://viewdns.info)
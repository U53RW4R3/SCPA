---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - dhcp
  - network-mapper
---
# DHCP

```
$ sudo nmap -sU -p 67 --script dhcp-discover <DHCP_server_IP>
```

These NSE scripts discovers the local network unless you want to scan the target externally.

```
$ sudo nmap --script broadcast-dhcp-discover [DHCP_server_IP]
```

^a89979

Scan IPv6 DHCP broadcast

```
$ sudo nmap -6 --script broadcast-dhcp6-discover [DHCP_server_IP]
```

---
## References

## Backlinks

- [[Denial of Service|Vulnerability Assessment: DHCP Denial of Service]]

### The Hacker Recipes

- [The Hacker Recipes: DHCP](https://www.thehacker.recipes/ad/recon/dhcp)
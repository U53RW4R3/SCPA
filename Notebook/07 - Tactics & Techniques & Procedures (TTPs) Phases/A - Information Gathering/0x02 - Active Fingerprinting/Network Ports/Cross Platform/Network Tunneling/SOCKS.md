---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - socks-proxy
  - network-protocols
  - socks
  - network-mapper
---
# SOCKS

> [!INFO]
> Unlike SOCKS4 protocol, SOCKS5 provides more options for authentication and has support for IPv6, UDP, and ICMP. DNS lookups are posssible. The only exception that TOR won't work due to security by design to prevent DNS leaks.

## 01 - Authentication Check

```
$ nmap -p 1080 -Pn -n --script socks-auth-info <IP>
```

## 02 - Detect Open SOCKS Proxy

```
$ nmap -p 1080 -Pn -n --script socks-open-proxy --script-args proxy.url=<host>,proxy.pattern=<pattern> <IP>
```

---
## References

### Backlinks

- [[01 - Scrape Proxies]]

- [[Proxychains]]

### Network Mapper

- [Network Mapper NSEDocs: socks-open-proxy Script](https://nmap.org/nsedoc/scripts/socks-open-proxy.html)

### Hacktricks

- [Hacktricks: 1080 - Pentesting Socks](https://book.hacktricks.wiki/en/network-services-pentesting/1080-pentesting-socks.html)
# Nmap

Search Tag(s): #active-reconnaissance #network-protocols #nmap

Note: unlike SOCKS4 protocol, SOCKS5 provides more options for authentication and has support for IPv6, UDP, and ICMP. DNS lookups are posssible. The only exception that TOR won't work due to security by design to prevent DNS leaks.

## Authentication Check

`$ nmap -p 1080 --script socks-auth-info <IP>`

---
## References

- [[Proxychains]]

- [Hacktricks: 1080 - Pentesting Socks](https://book.hacktricks.xyz/network-services-pentesting/1080-pentesting-socks)
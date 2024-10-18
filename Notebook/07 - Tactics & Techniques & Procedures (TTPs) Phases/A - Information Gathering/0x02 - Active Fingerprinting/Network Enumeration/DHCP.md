# DHCP

Search Tag(s): #active-reconnaissance #network-protocols #dhcp #network-mapper

```
$ sudo nmap -sU -p 67 --script dhcp-discover <IP>
```

These NSE scripts discovers the local network unless you want to scan the target externally.

```
$ sudo nmap --script broadcast-dhcp-discover [IP]
```

^a89979

Scan IPv6 DHCP broadcast

```
$ sudo nmap -6 --script broadcast-dhcp6-discover [IP]
```

---
## References

- [[Denial of Service|Vulnerability Assessment: DHCP Denial of Service]]
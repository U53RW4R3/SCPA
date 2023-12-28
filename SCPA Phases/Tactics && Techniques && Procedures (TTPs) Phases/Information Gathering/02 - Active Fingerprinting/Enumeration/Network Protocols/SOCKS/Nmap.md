# Nmap

Search Tag(s): #active-reconnaissance #network-protocols #socks #nmap

Note: unlike SOCKS4 protocol, SOCKS5 provides more options for authentication and has support for IPv6, UDP, and ICMP. DNS lookups are posssible. The only exception that TOR won't work due to security by design to prevent DNS leaks.

## Authentication Check

`$ nmap -p 1080 -Pn -n --script socks-auth-info <IP>`

## Detect Open SOCKS Proxy

```
$ nmap -p 1080 -Pn -n --script socks-open-proxy --script-args proxy.url=<host>,proxy.pattern=<pattern> <IP>

$ nmap -p 1080 -Pn -n -sS --max-retries 1 --min-parallelism 700 --open -T4 --script socks-open-proxy -iL targets.txt 2>/dev/null | grep -B 4 -A "socks-open-proxy:" | tee -a proxies-output.txt
```

---
## References

- [[Proxychains]]

- [Nmap NSEDocs: Script socks-open-proxy](https://nmap.org/nsedoc/scripts/socks-open-proxy.html)

- [Hacktricks: 1080 - Pentesting Socks](https://book.hacktricks.xyz/network-services-pentesting/1080-pentesting-socks)

### Hunt for Open Proxies

- [IP Address Location](https://www.ipaddresslocation.org/cidr/ip-ranges.php)

- [Fun Over IP: Socks proxy servers scanning with nmap](https://funoverip.net/2010/11/socks-proxy-servers-scanning-with-nmap/)
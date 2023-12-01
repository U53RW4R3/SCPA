# 01 - Proxychains

`$ cat tor.conf`

---

```
strict_chain
proxy_dns
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.1/255.255.255.255
[ProxyList]
socks4  127.0.0.1 9050
socks5  127.0.0.1 9050
```

- Lookup IP

```
$ curl https://ipinfo.io

$ curl https://ifconfig.me

$ curl https://ip.me
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/Post Exploitation/Shell Is The Beginning/Pivoting and Lateral Movement/Pivoting/Linux/SOCKS Proxy/Proxychains|Pivoting SOCKS Proxy with proxychains]]

- [Check TOR](https://check.torproject.org/)

- [Ifconfig.me](https://ifconfig.me/)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [Amazon AWS IP Lookup](checkip.amazonaws.com)
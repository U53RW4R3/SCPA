# 01 - Proxychains

```
$ cat tor.conf
strict_chain
proxy_dns
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.1/255.255.255.255
[ProxyList]
socks4  127.0.0.1 9050
socks5  127.0.0.1 9050
```

Lookup IP

```
$ proxychains curl https://ipinfo.io

$ proxychains curl https://ifconfig.me

$ proxychains curl https://ip.me

$ proxychains curl 'https://api.ipify.org?format=json'
```

Check if you're connected to TOR

```
$ proxychains -f tor.conf curl -s https://check.torproject.org/api/ip | jq -r .IsTor

$ proxychains -f tor.conf curl -s https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

- [[Proxychains|Pivoting SOCKS Proxy with proxychains]]

- [Check TOR](https://check.torproject.org/)

- [Ifconfig.me](https://ifconfig.me/)

- [Ifcfg.me](https://ifcfg.me)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [IPAPI](https://ipapi.co)

- [Amazon AWS IP Lookup](https://checkip.amazonaws.com)

- [IP API](https://ip-api.com)
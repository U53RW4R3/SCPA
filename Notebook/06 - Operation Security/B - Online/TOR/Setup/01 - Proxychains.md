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

$ proxychains curl https://ipecho.net/plain
```

Check if you're connected to TOR

```
$ proxychains -f tor.conf curl -s https://check.torproject.org/api/ip | jq -r .IsTor

$ proxychains -f tor.conf curl -s https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

### Backlinks

- [[Proxychains|Pivoting SOCKS Proxy with proxychains]]

### Check TOR Circuit

- [Check TOR](https://check.torproject.org/)

### Lookup IP

- [Ifconfig.me](https://ifconfig.me/)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [IPAPI](https://ipapi.co)

- [Amazon AWS IP Lookup](https://checkip.amazonaws.com)

- [IP API](https://ip-api.com)

- [IPv4.cat](https://about.ipv4.cat/)

- [IP Echo Service](https://ipecho.net)
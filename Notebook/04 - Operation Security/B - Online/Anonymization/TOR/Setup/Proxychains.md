# [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Post Exploitation/Pivoting/Linux/Proxychains|Proxychains]]

## 01 - Setup Configuration

Basic configuration file for `proxychains`.

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

## 02 - Lookup IP

```
$ proxychains -f tor.conf curl -s https://ipinfo.io

$ proxychains -f tor.conf curl -s https://ifconfig.me

$ proxychains -f tor.conf curl -s https://ifconfig.me/ip

$ proxychains -f tor.conf curl -s https://ip.me

$ proxychains -f tor.conf curl -s 'https://api.ipify.org?format=json' | jq

$ proxychains -f tor.conf curl -s https://ipecho.net/plain

$ proxychains -f tor.conf curl -s https://ipv4.icanhazip.com

$ proxychains -f tor.conf curl -s https://httpbin.org/ip | jq -r .origin
```

Check if you're connected to TOR

```
$ proxychains -f tor.conf curl -s https://check.torproject.org/api/ip | jq -r .IsTor

$ proxychains -f tor.conf curl -s https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x05 - Pivot/Linux/SOCKS Proxy/Proxychains|Post Exploitation: Proxychains]]

### Check TOR Circuit

- [Check TOR](https://check.torproject.org/)

### Aldeid

- [Aldeid: Nmap Scan Through Tor](https://www.aldeid.com/wiki/Tor/Usage/Nmap-scan-through-tor)

### Lookup IP

- [Ifconfig.me](https://ifconfig.me/)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [IPAPI](https://ipapi.co)

- [Amazon AWS IP Lookup](https://checkip.amazonaws.com)

- [IP API](https://ip-api.com)

- [IPv4.cat](https://about.ipv4.cat/)

- [IP Echo Service](https://ipecho.net)

- [ICanHazIP](https://icanhazip.com)

- [HTTPBin](https://httpbin.org)

### Open Dynamic Block Lists

- [Open Dynamic Block Lists](https://www.opendbl.net)
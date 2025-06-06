# 01 - Proxychains

## 1.1 - Setup

Install it according to your package manager.

```
$ sudo apt install -y proxychains4

$ sudo dnf install -y proxychains-ng

$ sudo pacman -S --noconfirm proxychains-ng
```

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

## 1.2 - Lookup IP

```
$ proxychains -f tor.conf curl -s https://ipinfo.io

$ proxychains -f tor.conf curl -s https://ifconfig.me

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

- [[Proxychains|Post Exploitation: Proxychains]]

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

- [ICanHazIP](https://icanhazip.com)

- [HTTPBin](https://httpbin.org)
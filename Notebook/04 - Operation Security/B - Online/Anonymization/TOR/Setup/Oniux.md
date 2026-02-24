# Oniux

## 3.1 - Setup

### 3.1.1 - Package Manager

Install it according to your package manager.

```
$ yay -S --noconfirm oniux
```

### 3.1.2 - Universal Install

```
$ cargo install --git https://gitlab.torproject.org/tpo/core/oniux oniux@0.4.0
```

## 3.2 - Lookup IP

```
$ oniux curl -s https://ipinfo.io

$ oniux curl -s https://ifconfig.me

$ oniux curl -s https://ifconfig.me/ip

$ oniux curl -s https://ip.me

$ oniux curl -s 'https://api.ipify.org?format=json'

$ oniux curl -s https://ipecho.net/plain

$ oniux curl -s https://ipv4.icanhazip.com

$ oniux curl -s https://httpbin.org/ip | jq -r .origin
```

Check if you're connected to TOR

```
$ oniux curl -s https://check.torproject.org/api/ip | jq -r .IsTor

$ oniux curl -s https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

### Source Repositories

- [oniux](https://gitlab.torproject.org/tpo/core/oniux)

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

### Open Dynamic Block Lists

- [Open Dynamic Block Lists](https://www.opendbl.net)
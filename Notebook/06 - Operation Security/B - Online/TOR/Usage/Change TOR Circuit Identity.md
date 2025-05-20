# Change TOR Circuit Identity

Change TOR Identity.

```
$ killall -HUP tor
```

If that does not work, enable the control port in your torrc file. Then, set a password for the control port with `tor --hash-password <password>`.

```
$ echo -e 'AUTHENTICATE "<password>"\r\nSIGNAL NEWNYM\r\nQUIT' | nc 127.0.0.1 9051

$ printf 'AUTHENTICATE "<password>"\r\nSIGNAL NEWNYM\r\n' | nc 127.0.0.1 9051
```

Lookup IP.

```
$ curl --socks5 127.0.0.1:9050 https://iconfig.me

$ curl --socks5 127.0.0.1:9050 https://ip.me

$ curl --socks5 127.0.0.1:9050 https://ipinfo.io

$ curl --socks5 127.0.0.1:9050 https://checkip.amazonaws.com/

$ curl --socsk5 127.0.0.1:9050 https://ipecho.net/plain
```

Check if you're connected to TOR.

```
$ curl -s --socks5 127.0.0.1:9050 https://check.torproject.org/api/ip | jq -r .IsTor

$ curl -s --socks5 127.0.0.1:9050 https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

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
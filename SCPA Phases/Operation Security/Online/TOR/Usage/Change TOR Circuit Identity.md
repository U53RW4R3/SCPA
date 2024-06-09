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
$ curl --socks5 127.0.0.1:9050 https://checkip.amazonaws.com/
```

Check if you're connected to TOR.

```
$ curl -s https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

- [Check TOR](https://check.torproject.org/)

- [Ifconfig.me](https://ifconfig.me/)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [Amazon AWS IP Lookup](checkip.amazonaws.com)
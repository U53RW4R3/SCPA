# Manual

## 01 - Whois

```
$ whois <domain.com>

$ whois -I <domain.com>

$ whois -a -T inetnum <organization_name>
```

## 02 - Telnet

```
$ telnet whois.iana.org 43
<domain.com>
```

## 03 - Netcat

`$ echo <domain.com> | nc whois.iana.org 43`

---
## References

- [Hacker Target: Whois Lookup](https://hackertarget.com/whois-lookup/)
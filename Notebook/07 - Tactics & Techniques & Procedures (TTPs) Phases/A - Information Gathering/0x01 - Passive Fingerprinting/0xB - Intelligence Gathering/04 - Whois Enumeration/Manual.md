# Manual

## 01 - Whois

```
$ whois <domain.com>

$ whois -I <domain.com>

$ whois -a -T inetnum <organization_name>
```

### 1.1 - Cymru

```
$ whois -h whois.cymru.com "-v <IP>"
```

### 1.2 - Shadowserver

Retrieve the ASN name and ID.

```
$ curl -s https://api.shadowserver.org/net/asn?origin=<IP> | jq

$ whois -h asn.shadowserver.org 'origin <IP>'
```

Retrieve the IP with CIDR and ASN ID along with it's peers.

```
$ curl -s https://api.shadowserver.org/net/asn?peer=<IP> | jq

$ whois -h asn.shadowserver.org 'peer <IP> verbose'
```

## 02 - Telnet

```
$ telnet whois.iana.org 43
<domain.com>
```

## 03 - Netcat

```
$ echo <domain.com> | nc whois.iana.org 43
```

---
## References

- [Hacker Target: Whois Lookup](https://hackertarget.com/whois-lookup/)
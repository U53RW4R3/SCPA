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

```
$ curl -s https://api.shadowserver.org/net/asn?origin=<IP> | jq
```

Retrieve the ASN ID.

```
$ curl -s https://api.shadowserver.org/net/asn?origin=<IP> | jq '.[0].asn'

$ curl -s https://api.shadowserver.org/net/asn?origin=<IP> | jq '.[0].asn_name'

$ whois -h asn.shadowserver.org 'origin <IP>'

$ whois -h asn.shadowserver.org 'origin <IP>' | grep -Eo "AS[0-9]+"
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
$ nc whois.iana.org 43 <<< "<domain>.<tld>"

$ echo <domain.com> | nc whois.iana.org 43
```

---
## References

- [Hacker Target: Whois Lookup](https://hackertarget.com/whois-lookup/)
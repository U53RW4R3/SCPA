# Manual

## Hurricane

Hurricane Electric Internet Services to retrieve IP address.

```
$ curl -A <user_agent> -s "https://bgp.he.net/search?search\[search\]=<query>&commit=Search" | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}"
```

## RIPEstate

```
$ curl -s https://stat.ripe.net/data/announced-prefixes/data.json?resource=<asn_ID> | jq -r '.data.prefixes[].prefix' > ip_target_ranges.txt

$ whois -h riswhois.ripe.net <IP>
```

## IPInfo

```
$ curl -s https://ipinfo.io/<IP>

$ curl -s ipinfo.io/<IP>/json | jq
```

Google dork.

```
site:ipinfo.io "<organization_name>"
```

## IPAPI

```
$ curl -s https://ipapi.co/<IP>/json/' | jq -r .asn
```

## Shadowserver

ASN ID.

```
$ whois -h asn.shadowserver.org 'prefix <ASN_ID>'

$ curl -s https://api.shadowserver.org/net/asn?prefix=<ASN_ID> | jq -r '.[]'

$ curl -s https://api.shadowserver.org/net/asn?prefix=<ASN_ID> | jq | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}"

$ nc asn.shadowserver.org 43 < ips.txt > asn.txt
```

## RADb

```
$ whois -h whois.radb.net -- '-i origin <ASN_ID>' | grep -Eo "([0-9.]+){4}/[0-9]+" | sort -u
```

---
## References

### Sidxparab

- [Sidxparab: Horizontal Enumeration](https://sidxparab.gitbook.io/subdomain-enumeration-guide/types/horizontal-enumeration)

### Hurricane

- [Hurricane Electric Internet Services](https://bgp.he.net/)

### RIPEstat

- [RIPEstat](https://stat.ripe.net)

### BGP Ranking

- [BGP Ranking](https://bgpranking.circl.lu/)

### PeeringDB

- [PeeringDB](https://www.peeringdb.com/)

### IPInfo

- [IPInfo: Developers](https://ipinfo.io/developers)

### IPAPI

- [IPAPI](https://ipapi.co)

### ShadowServer

- [ShadowServer](https://www.shadowserver.org/)

### ASNLookup

- [ASNLookup](https://asnlookup.com/)
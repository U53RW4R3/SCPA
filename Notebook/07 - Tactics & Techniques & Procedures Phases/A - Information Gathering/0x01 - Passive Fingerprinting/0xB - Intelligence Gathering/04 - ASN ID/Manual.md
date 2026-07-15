# Manual

## Hurricane

Hurricane Electric Internet Services to retrieve IP address.

```
$ curl -A <user_agent> -s "https://bgp.he.net/search?search\[search\]=<query>&commit=Search" | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}"
```

## RIPEstate

```
$ curl -s https://stat.ripe.net/data/announced-prefixes/data.json?resource=<asn_ID> | jq -r '.data.prefixes[].prefix' > ip_target_ranges.txt

$ whois -H -h riswhois.ripe.net <IP>
```

## IPInfo

```
$ curl -s https://ipinfo.io/<IP>

$ curl -s https://ipinfo.io/<IP>/json | jq

$ curl -s https://ipinfo.io/<IP>/json | jq -r '.prefixes[].netblock' | tr -d \"

$ curl -s ipinfo.io/<IP>/json | python -m json.tool
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
$ whois -H -h asn.shadowserver.org 'prefix <ASN_ID>'

$ curl -s https://api.shadowserver.org/net/asn?prefix=<ASN_ID> | jq -r '.[]'

$ curl -s https://api.shadowserver.org/net/asn?prefix=<ASN_ID> | jq | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}"

$ curl -s https://api.shadowserver.org/net/asn?prefix=<ASN_ID> | python -m json.tool | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}"

$ nc asn.shadowserver.org 43 < ips.txt > asn.txt
```

## Cymru

```
$ whois -H -h whois.cymru.com "-v <ASN_ID>"
```

Scanning a bulk of ASN IDs.

```
$ cat > asns.txt << EOF
begin
verbose
as23028
as<ID>
end

$ nc whois.cymru.com 43 < asns.txt > output.txt
```

A short script to automate recon.

```bash
asn() {
  [[ -n $1 ]] && { echo -e "begin\nverbose\n${1}\nend" | nc whois.cymru.com 43 | tail -n +2; return; }
  (echo -e 'begin\nverbose'; cat -; echo end) | nc whois.cymru.com 43 | tail -n +2
}
```

The usage of the script as it follows.

```
$ asn <IP>

$ asn < ips.txt
```

## RADb

```
$ whois -H -h whois.radb.net -- '-i origin <ASN_ID>' | grep -Eo "([0-9.]+){4}/[0-9]+" | sort -uo netblocks.txt
```

---
## References

### Source Repository

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

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

### Cymru

- [Cymru: IP ASN Mapping](https://www.team-cymru.com/ip-asn-mapping)

### ASNLookup

- [ASNLookup](https://asnlookup.com/)

### DNSChecker

- [DNSChecker: DNS Lookup](https://dnschecker.org/all-dns-records-of-domain.php)

- [DNSChecker: ASN Lookup](https://dnschecker.org/asn-whois-lookup.php)

### CAIDA

- [CAIDA: AS Rank](https://asrank.caida.org/)
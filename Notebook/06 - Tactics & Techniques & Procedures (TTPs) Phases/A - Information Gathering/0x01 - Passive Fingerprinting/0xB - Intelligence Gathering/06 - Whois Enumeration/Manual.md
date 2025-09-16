# Manual

## 01 - Whois

```
$ whois <domain.com>

$ whois -I <domain.com>

$ whois -a -T inetnum <organization_name>
```

### 1.1 - APNIC

```
$ whois -h whois.apnic.net <organization_name>
```

### 1.2 - Cymru

```
$ whois -h whois.cymru.com "-v <IP>"
```

Scanning a bulk of IP addresses.

```
$ cat > ips.txt << EOF
begin
68.22.187.5
207.229.165.18
end

$ nc whois.cymru.com 43 < ips.txt | sort -n > ASN_ID.txt
```

### 1.3 - Shadowserver

```
$ curl -s https://api.shadowserver.org/net/asn?origin=<IP> | jq

$ curl -s https://api.shadowserver.org/net/asn?origin=<IP> | python -m json.tool
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

$ curl -s https://api.shadowserver.org/net/asn?peer=<IP> | python -m json.tool

$ whois -h asn.shadowserver.org 'peer <IP> verbose'
```

### 1.4 - RADb

```
$ whois -h whois.radb.net -- '-i origin <ASN_ID>'
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

### Qazeer

- [Qazeer: External Recon](https://notes.qazeer.io/general/external_recon)

### Hacker Target

- [Hacker Target: Whois Lookup](https://hackertarget.com/whois-lookup/)

### APNIC

- [APNIC](https://www.apnic.net/)

### Cymru

- [Cymru: IP ASN Mapping](https://www.team-cymru.com/ip-asn-mapping)
# 02 - Basic Queries

## 2.1 - ANY

Use every DNS type to retrieve information of the domain.

```
$ dig ANY <domain>.<tld> @<DNS_IP>

$ host -v -t ANY <domain>.<tld>

> nslookup -type=ANY <domain>.<tld>
```

## 2.2 - NameServer (NS)

Query the primary IP address of the **Nameserver (NS)**.

```
$ dig NS <domain>.<tld> @<DNS_IP>

$ host -t NS <domain>.<tld>

> nslookup -type=NS <domain>.<tld>
```

## 2.3 - IPv4 Address (A)

Getting the **IPv4 address (A)** of the organization's domain website.

```
$ dig A <domain>.<tld> @<DNS_IP>

$ host -t A <domain>.<tld>

> nslookup -type=A <domain>.<tld>
```

## 2.4 - IPv6 Address (AAAA)

Getting the **IPv6 address (AAAA)** of the organization's domain website.

```
$ dig AAAA <domain>.<tld> @<DNS_IP>

$ host -t AAAA <domain>.<tld>

> nslookup -type=AAAA <domain>.<tld>
```

## 2.5 - Mail eXchange (MX)

Discovering the **Mail eXchange (MX)** Servers.

```
$ dig MX <domain>.<tld> @<DNS_IP>

$ host -t MX <domain>.<tld>

> nslookup -type=MX <domain>.<tld>
```

## 2.6 - Canonical Name (CNAME)

Query the **Canonical Name (CNAME)** of the website.

```
$ dig CNAME www.<domain>.<tld> @<DNS_IP>

$ host -t CNAME www.<domain>.<tld>

> nslookup -type=CNAME www.<domain>.<tld>
```

## 2.7 - CertifiCate Authorities (CAA)

Discover **CertifiCate Authorities (CAA)** that Issues Certificates of the domain.

```
$ dig CAA <domain>.<tld> @<DNS_IP>

$ host -t CAA <domain>.<tld>

> nslookup -type=CAA <domain>.<tld>
```

## 2.8 - LOCation (LOC)

Find the physical Geographical **LOCation** **(LOC)** of the domain.

```
$ dig LOC <domain>.<tld> @<DNS_IP>

$ host -t LOC <domain>.<tld>

> nslookup -type=LOC <domain>.<tld>
```

## 2.9 - Text Record (TXT)

Query the **Text Record (TXT)** information of the domain.

```
$ dig TXT <domain>.<tld> @<DNS_IP>

$ host -t TXT <domain>.<tld>

> nslookup -type=TXT <domain>.<tld>
```

## 2.10 - DMARC

```
$ dig TXT _dmarc.<domain>.<tld> @<DNS_IP>

$ host -t TXT _dmarc.<domain>.<tld>

> nslookup -type=TXT _dmarc.<domain>.<tld>
```

## 2.11 - Service Record (SRV)

Retrieve the **Service Record (SRV)** domain.

```
> nslookup -type=srv _sip._tcp.<domain>.<tld> <DNS_IP>
```

Lookup the **IP's SIP server** of the domain.

```
$ dig A sip.<domain>.<tld> @<DNS_IP>

$ host -t A sip.<domain>.<tld>

> nslookup -type=A sip.<domain>.<tld>
```

## 2.12 - Zone of Authority Record (SOA)

Finding the administrative email which is the **zone of authority record (SOA)** of the domain

```
$ dig SOA <domain>.<tld> @<DNS_IP>

$ host -t SOA <domain>.<tld>

$ host -C <domain>.<tld>

> nslookup -type=SOA <domain>.<tld>
```

## 2.13 - Pointer (PTR)

Enumerate the domain's source **Pointer (PTR)** IP address that corresponds to

```
$ dig -x <PTR_IP> @<DNS_IP>
```

## 2.14 - SPF

```
$ dig SPF <domain>.<tld> @<DNS_IP>

$ host -t SPF <domain>.<tld>

> nslookup -type=SPF <domain>.<tld>
```

## 2.15 - Host Information Records (HINFO)

```
$ dig HINFO <domain>.<tld>

$ host -t HINFO <domain>.<tld>

> nslookup -type=HINFO <domain>.<tld>
```

## 2.16 - Integrated Services Digital Network Records (ISDN)

```
$ dig ISDN <domain>.<tld>

$ host -t ISDN <domain>.<tld>

> nslookup -type=ISDN <domain>.<tld>
```

---
## References

### Backlinks

- [[References DNS Records]]

### Hacktricks

- [Hacktricks: Pentesting DNS](https://book.hacktricks.xyz/pentesting/pentesting-dns)
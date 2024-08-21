# 02 - Basic Queries

## 2.1 - ANY

Use every DNS type to retrieve information of the domain.

```
$ dig ANY <domain.com> @<DNS_IP>

$ host -v -t ANY <domain.com>

> nslookup -type=any <domain.com>
```

## 2.2 - NameServer (NS)

Query the primary IP address of the **Nameserver (NS)**.

```
$ dig NS <domain.com> @<DNS_IP>

$ host -t NS <domain.com>

> nslookup -type=ns <domain.com>
```

## 2.3 - IPv4 Address (A)

Getting the **IPv4 address (A)** of the organization's domain website.

```
$ dig A <domain.com> @<DNS_IP>

$ host -t A <domain.com>

> nslookup -type=a <domain.com>
```

## 2.4 - IPv6 Address (AAAA)

Getting the **IPv6 address (AAAA)** of the organization's domain website

```
$ dig AAAA <domain.com> @<DNS_IP>

$ host -t AAAA <domain.com>

> nslookup -type=aaaa <domain.com>
```

## 2.5 - Mail eXchange (MX)

Discovering the **Mail eXchange (MX)** Servers.

```
$ dig MX <domain.com> @<DNS_IP>

$ host -t MX <domain.com>

> nslookup -type=mx <domain.com>
```

## 2.6 - Canonical Name (CNAME)

Query the **Canonical Name (CNAME)** of the website

```
$ dig CNAME <www.domain.com> @<DNS_IP>

$ host -t CNAME <www.domain.com>

> nslookup -type=cname <www.domain.com>
```

## 2.7 - CertifiCate Authorities (CAA)

Discover **CertifiCate Authorities (CAA)** that Issues Certificates of the domain

```
$ dig CAA <domain.com> @<DNS_IP>

$ host -t CAA <domain.com>

> nslookup -type=caa <domain.com>
```

## 2.8 - LOCation (LOC)

Find the physical Geographical **LOCation** **(LOC)** of the domain

```
$ dig LOC <domain.com> @<DNS_IP>

$ host -t LOC <domain.com>

> nslookup -type=loc <domain.com>
```

## 2.9 - Text Record (TXT)

Query the **Text Record (TXT)** information of the domain

```
$ dig TXT <domain.com> @<DNS_IP>

$ host -t TXT <domain.com>

> nslookup -type=txt <domain.com>
```

## 2.10 - Service Record (SRV)

Retrieve the **Service Record (SRV)** domain.

```
> nslookup -type=srv _sip._tcp.<domain.com> <DNS_IP>
```

- Lookup the **IP's SIP server** of the domain

```
$ dig A <sip.domain.com> @<DNS_IP>

$ host -t A <sip.domain.com>

> nslookup -type=a <sip.domain.com>
```

## 2.11 - Zone of Authority Record (SOA)

Finding the administrative email which is the **zone of authority record (SOA)** of the domain

```
$ dig SOA <domain.com> @<DNS_IP>

$ host -t SOA <domain.com>

$ host -C <domain.com>

> nslookup -type=SOA <domain.com>
```

## 2.12 - Pointer (PTR)

Enumerate the domain's source **Pointer (PTR)** IP address that corresponds to

```
$ dig -x <PTR_IP> @<DNS_IP>
```

## 2.13 - Reverse DNS Lookup

- Using nslookup performing a reverse dns lookups on the internal network

```
> nslookup -type=<DNS_record_type>

> server <IP_DNS>
> <target_IP>
```
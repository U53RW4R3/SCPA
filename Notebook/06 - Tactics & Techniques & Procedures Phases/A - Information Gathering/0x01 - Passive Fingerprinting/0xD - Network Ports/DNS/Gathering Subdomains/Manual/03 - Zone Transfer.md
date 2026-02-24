# 03 - Zone Transfer

## 3.1 - AXFR

Query the IP without the domain name with records of subdomains and other IP addresses (`axfr`)

```
$ dig axfr @<DNS_IP>

$ host -l <domain>.<tld> @<DNS_IP> | grep 'has address' | awk '{print $1}'
```

## 3.2 - LDAP Server

Lookup the **IP's LDAP server** of the domain

```
$ nslookup -type=srv _ldap._tcp.<domain>.<tld> @<DNS_IP>

$ dig A ldap.<domain>.<tld> @<DNS_IP>

$ dig axfr <domain>.<tld> @<DNS_IP>
```

## 3.3 - Reverse DNS via IPv4

Enumerate the subdomain's that only reverse DNS entry exists for the domain with IPv4 addresses (for example it owns **`192.168.*.*`**)

```
$ dig axfr -x 192.168 @<DNS_IP>
```

## 3.4 - Reverse DNS via IPv6

Enumerate the subdomain's that only reverse DNS entry exists for the domain with IPv6 addresses

```
$ dig axfr -x 2a00:1450:400c:c06::93 @<DNS_IP>
```

Enumerate DNS subdomains via zonetransfer via `host`.

```
$ host -l <domain.com> <dns_nameserver>
```

---
## References

### Backlinks

- [[References DNS Records]]

### Hacktricks

- [Hacktricks: Pentesting DNS](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-dns.html)
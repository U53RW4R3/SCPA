# Manual

Pipe it to IPv4 addresses.

```
$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" | cut -d ' ' -f 4 | sort -u > ip_targets.txt

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" | cut -d ' ' -f 4 | sort -u > ip_targets.txt

$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" | awk "{print $4}" | sort -u > ip_targets.txt

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" | awk "{print $4}" | sort -u > ip_targets.txt
```

---
## References

### Hacktricks

- [Hacktricks: Pentesting DNS](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-dns.html)

### Sidxparab

- [Sidxparab: Vertical Enumeration](https://sidxparab.gitbook.io/subdomain-enumeration-guide/types/vertical-enumeration)
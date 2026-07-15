# Manual

```
$ for domain in $(cat subdomains.txt); do host $domain | grep "has address"

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address"
```

---
## References

### Sidxparab

- [Sidxparab: Vertical Enumeration](https://sidxparab.gitbook.io/subdomain-enumeration-guide/types/vertical-enumeration)

### Wordlist

- [Assetnote Wordlists: Best DNS Wordlist](https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt)
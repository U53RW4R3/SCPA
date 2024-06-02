# Manual

```
$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" --color=auto

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" --color=auto
```

---
## References

### Wordlist

- [Assetnote Wordlists: Best DNS Wordlist](https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt)
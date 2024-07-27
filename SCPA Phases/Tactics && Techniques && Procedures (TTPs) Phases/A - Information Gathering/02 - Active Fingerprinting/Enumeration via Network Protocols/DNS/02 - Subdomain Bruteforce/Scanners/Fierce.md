# Fierce

```
$ fierce --domain <domain.com> --dictionary wordlist.txt | grep Found | tee output.txt
```

Extract subdomains

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' output.txt > subdomains.txt
```

Extract IPs

```
$ awk -F ". " '{print $3}' output.txt | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | sort -u ip_targets.txt
```

---
## References

- [[Domains]]

### Wordlist

- [Assetnote Wordlists: Best DNS Wordlist](https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt)
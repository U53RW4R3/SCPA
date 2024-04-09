# DNSx

```
$ dnsx -d <domain>.FUZZ -w wordlist.txt -resp

$ for domain in $(cat domains.txt); do dnsx -silent -d FUZZ.$domain -w wordlist.txt -o $domain.txt; done
```
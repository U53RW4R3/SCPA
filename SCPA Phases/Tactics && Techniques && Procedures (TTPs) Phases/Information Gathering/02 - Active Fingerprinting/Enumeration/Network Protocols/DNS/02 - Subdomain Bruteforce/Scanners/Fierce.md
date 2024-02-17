# Fierce

`$ fierce --domain <domain.com> --dictionary wordlist.txt | grep Found | tee output.txt`

- Extract subdomains

`$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' output.txt > subdomains.txt`

- Extract IPs

```
$ awk -F ". " '{print $3}' output.txt | grep -Eo "(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)" | sort -u ip_targets.txt
```
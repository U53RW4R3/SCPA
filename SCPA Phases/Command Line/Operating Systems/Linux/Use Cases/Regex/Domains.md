# Domains

## Subdomains

### Gather Subdomains

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' file.txt | sort -u > subdomains-output.txt
```
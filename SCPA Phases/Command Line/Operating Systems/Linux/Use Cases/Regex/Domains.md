# Domains

Search Tag(s): #use-cases #command-line #networking #regex #linux

## Subdomains

### Extract Subdomains

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' file.txt | sort -u > subdomains-output.txt
```
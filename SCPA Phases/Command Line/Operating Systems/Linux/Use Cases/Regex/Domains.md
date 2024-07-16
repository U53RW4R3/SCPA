# Domains

Search Tag(s): #use-cases #command-line #networking #regex #linux

## Extract Subdomains

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' file.txt | sort -u > subdomains-output.txt
```

## Strip URI

```
$ grep -Po '^(.*://[^/]+)/' file.txt
```

---
## References

- [[Linux Commands References]]
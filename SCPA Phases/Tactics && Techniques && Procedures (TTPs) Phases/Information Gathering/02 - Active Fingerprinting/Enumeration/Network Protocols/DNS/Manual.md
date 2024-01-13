# Manual

```
$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" --color=auto

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" --color=auto
```

- Pipe it to IPv4 addresses

```
$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" | cut -d ' ' -f 4 | sort | uniq > ip_targets.txt

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" | cut -d ' ' -f 4 | sort | uniq > ip_targets.txt

$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" | awk "{print $4}" | sort | uniq > ip_targets.txt

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" | awk "{print $4}" | sort | uniq > ip_targets.txt
```

---
## References

- [Hacktricks: Pentesting DNS](https://book.hacktricks.xyz/pentesting/pentesting-dns)
# Manual

```
$ for domain in $(cat subdomains.txt); do host $domain | grep "has address" --color=auto

$ cat subdomains.txt | xargs -P 10 -I {} host {} | grep "has address" --color=auto
```
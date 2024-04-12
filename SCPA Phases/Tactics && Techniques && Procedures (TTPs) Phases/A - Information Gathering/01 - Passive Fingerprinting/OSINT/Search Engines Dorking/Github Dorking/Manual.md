# Manual

## 01 - API Keys

AWS

```
path:.env AWS_KEY /(AKIA[A-Z0-9]{12,})/
```

Shodan

```
shodan_api_key
```

Intelx

```
intelx /([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})/
```

## 02 - CS Github

`cs.github.com`

## 03 - Network Protocols

```
/ssh:\/\/.*:.*@.*target\.com/

/ftp:\/\/.*:.*@.*target\.com/
```

---
## References

- [Hacktricks: Github Dorks & Leaks](https://book.hacktricks.xyz/generic-methodologies-and-resources/external-recon-methodology/github-leaked-secrets)

- [Techgaun: Github Dorks](https://github.com/techgaun/github-dorks)
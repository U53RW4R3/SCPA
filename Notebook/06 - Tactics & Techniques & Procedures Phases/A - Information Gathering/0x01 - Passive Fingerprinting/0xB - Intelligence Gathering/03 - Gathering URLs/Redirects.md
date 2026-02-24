# Redirects

TODO: Include `ipinfo.io`

```
$ curl -s "https://host.io/api/domains/redirects/<domain>.<tld>?&limit=1000" | jq -r '.domains' | jq '.[]' | tr -d "\\" > redirects.txt
```

---
## References

### Host.io

- [Domain Name Data - host.io](https://host.io)
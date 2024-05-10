# Manual

```
$ curl -s "https://api.certspotter.com/v1/issuances?domain=<domain.com>&include_subdomains=true&expand=dns_names" | jq -r '.[].dns_names[]' | sort -u
```

- Provide certificate issuer.

```
$ curl -s "https://api.certspotter.com/v1/issuances?domain=<domain.com>&include_subdomains=true&expand=dns_names&expand=issuer" | jq -r '.[].dns_names[]' | sort -u
```

---
## References

- [SSLMate](https://sslmate.com/ct_search_api/)
# AlienVault

```
$ curl -s "https://otx.alienvault.com/api/v1/indicators/hostname/<domain>.<tld>/url_list?limit=500&page=1" | jq -r '.url_list[]?.result?.urlworker?.ip // empty' | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' | sort -uo ips.txt
```

---
## References

### AlienVault

- [AlienVault](https://otx.alienvault.com/)
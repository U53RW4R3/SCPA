# URLScan

```
$ curl -s "https://urlscan.io/api/v1/search/?q=domain:<domain>.<tld>&size=10000" | jq -r '.results[]?.page?.ip // empty' | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' | sort -uo ips.txt
```

---
## References

### URLScan

- [URLScan](https://urlscan.io)
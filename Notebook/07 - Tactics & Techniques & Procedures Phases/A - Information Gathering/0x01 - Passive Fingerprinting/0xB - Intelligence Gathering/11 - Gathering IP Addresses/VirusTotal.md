# VirusTotal

```
$ curl -s "https://www.virustotal.com/vtapi/v2/domain/report?domain=<domain>.<tld>&apikey=<api_key>" | jq -r '.. | .ipaddress? // empty' | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' | sort -uo ips.txt
```

---
## References

### VirusTotal

- [VirusTotal](https://www.virustotal.com)
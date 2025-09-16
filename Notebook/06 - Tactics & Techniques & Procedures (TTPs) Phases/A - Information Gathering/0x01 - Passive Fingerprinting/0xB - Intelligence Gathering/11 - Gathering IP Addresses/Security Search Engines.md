# Security Search Engines

## Shodan

```
$ shodan domain domain.tld | grep ([0-9]{1,3}\.){3}[0-9]{1,3} | sort -uo ip_targets.txt
```

## Censys

```
$ curl -g -X 'GET' \
'https://search.censys.io/api/v2/hosts/search?per_page=<pages>&virtual_hosts=EXCLUDE&sort=RELEVANCE&q=<censys_query_search>' \
-H 'Accept: application/json' \
--user "<censys_API_ID>:<censys_API_SECRET>" | jq > censys-output.json
```

```
$ grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" censys-output.json | sort -uo ip_targets.txt
```

---
## References

### Backlinks

- [[Shodan Usage]]

- [[Censys Usage]]
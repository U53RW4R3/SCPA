---
author(s):
  - Userware
tags:
  - information-gathering
  - passive-fingerprinting
  - security-search-engine
  - censys
---
# Censys Usage

> [!NOTE]
> The maximum pages is 100 when you're using a free version.

## 01 - Usage Queries

Country Code.

```
location.country= `Russia`
```

## 02 - CLI Usage

```
$ curl -g -X 'GET' \
'https://search.censys.io/api/v2/hosts/search?per_page=<pages>&virtual_hosts=EXCLUDE&sort=RELEVANCE&q=<censys_query_search>' \
-H 'Accept: application/json' \
--user "<censys_API_ID>:<censys_API_SECRET>" | jq > censys-output.json

$ curl -g -X 'GET' \
'https://search.censys.io/api/v2/hosts/search?per_page=<pages>&virtual_hosts=EXCLUDE&sort=RELEVANCE&q=<censys_query_search>' \
-H 'Accept: application/json' \
--user "<censys_API_ID>:<censys_API_SECRET>" | python -m json.tool > censys-output.json
```

---
## References

- [Censys.io](https://search.censys.io/)

- [Censys: Host Query Examples](https://support.censys.io/hc/en-us/articles/360059720271-Host-Query-Examples)

- [Censys: Search Host Query Mindmap](https://censys.com/wp-content/uploads/2023/10/Censys-Search-Host-Queries.pdf)
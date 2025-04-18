# Censys Usage

Search Tag(s): #information-gathering #search-engine #censys

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
```

### 2.1 - Retrieve IP Addresses

```
$ grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" censys-output.json | sort -uo ip_targets.txt
```

---
## References

- [Censys.io](https://search.censys.io/)

- [Censys: Host Query Examples](https://support.censys.io/hc/en-us/articles/360059720271-Host-Query-Examples)

- [Censys: Search Host Query Mindmap](https://censys.com/wp-content/uploads/2023/10/Censys-Search-Host-Queries.pdf)
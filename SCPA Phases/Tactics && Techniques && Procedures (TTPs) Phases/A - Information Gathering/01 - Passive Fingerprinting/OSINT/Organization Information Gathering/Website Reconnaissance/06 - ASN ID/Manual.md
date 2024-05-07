# Manual

- Hurricane Electric Internet Services to retrieve IP address

```
$ curl -A <user_agent> -s "https://bgp.he.net/search?search\[search\]=<query>&commit=Search" | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}\b"
```

- RIPEstate

```
$ curl -s https://stat.ripe.net/data/announced-prefixes/data.json?resource=<asn_ID> | jq -r '.data.prefixes[].prefix' > ip_target_ranges.txt
```

---
## References

 - [Hurricane Electric Internet Services](https://bgp.he.net/)
 
 - [RIPEstat](https://stat.ripe.net)
 
 - [BGP Ranking](https://bgpranking.circl.lu/)

- [PeeringDB](https://www.peeringdb.com/)
# Manual

TODO: Issue a POST request with curl to lookup organization names for `bgp.he.net`

```
$ curl --silent https://stat.ripe.net/data/announced-prefixes/data.json?resource=<asn_ID> | jq -r '.data.prefixes[].prefix' > ip_target_ranges.txt
```

---
## References

 - [Hurricane Electric Internet Services](https://bgp.he.net/)
 
 - [RIPEstat](https://stat.ripe.net)
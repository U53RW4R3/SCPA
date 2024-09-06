# Nmap

```
$ nmap -sn -Pn -n --script shodan-api --script-args 'shodan-api.apikey=<API_KEY>,shodan-api.outfile=shodan-output.csv' <IP>/<CIDR>

$ nmap --script shodan-api --script-args 'shodan-api.apikey=<API_KEY>,shodan-api.target=<IP>,shodan-api.outfile=shodan-output.csv'
```

---
## References

- [Shodan-API NSE Script](https://nmap.org/nsedoc/scripts/shodan-api.html)
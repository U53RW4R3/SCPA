# Manual

- Certificate Transparency (CT) Logs

`$ curl -s -s "https://crt.sh/?cn=<domain.com>&output=json" | jq -r '.[].name_value' | sort -u`

- tls.bufferover.run

```
$ curl 'https://tls.bufferover.run/dns?q=.example.com' -H 'x-api-key: <tls.bufferover.run_API_key>' | jq -r .Results[] | cut -d ',' -f5 | sort -u
```

---
## References

- [Certificate Transparency (CT) Logs](https://crt.sh)

- [tls.bufferover.run](https://tls.bufferover.run/)
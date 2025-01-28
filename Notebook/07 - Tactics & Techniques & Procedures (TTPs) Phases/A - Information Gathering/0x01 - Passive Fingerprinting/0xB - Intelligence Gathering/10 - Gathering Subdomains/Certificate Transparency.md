# Certificate Transparency

## Certificate Check

### Manual

Certificate Transparency (CT) Logs

```
$ curl -s "https://crt.sh/?cn=<domain>.<tld>&output=json" | jq -r '.[].name_value' | sort -u

$ curl -s "https://crt.sh/?o=<organization_name>&output=json" | jq -r '.[].common_name' | sort -u
```

TLS bufferover

```
$ curl 'https://tls.bufferover.run/dns?q=.<domain>.<tld>' -H 'x-api-key: <tls.bufferover.run_API_key>' | jq -r .Results[] | cut -d ',' -f5 | sort -u
```

### DNSRecon

```
$ dnsrecon -d <domain>.<tld> -t crt
```

### Sn0int

```
[sn0int][default] > install kpcyrd/ctlogs

[sn0int][default] > use kpcyrd/ctlogs

[sn0int][default][kpcyrd/ctlogs] > run
```

### Network Mapper

```
$ nmap -Pn --script hostmap-crtsh --script-args 'hostmap-crtsh.prefix=hostmap-' <IP>

$ nmap -sn --script hostmap-crtsh <IP>
```

## SSL Server Test

### Manual

```
$ curl -s "https://api.certspotter.com/v1/issuances?domain=<domain>.<tld>&include_subdomains=true&expand=dns_names" | jq -r '.[].dns_names[]' | sort -u
```

Provide certificate issuer.

```
$ curl -s "https://api.certspotter.com/v1/issuances?domain=<domain.com>&include_subdomains=true&expand=dns_names&expand=issuer" | jq -r '.[].dns_names[]' | sort -u
```

### Recon-ng

- `ssl_scan` recon-ng module

```
[recon-ng][default] > marketplace install recon/ports-hosts/ssl_scan

[recon-ng][default] > modules load recon/ports-hosts/ssl_scan

[recon-ng][default][ssl_scan] > options set SOURCE <domain.com>:443

[recon-ng][default][ssl_scan] > options set SOURCE /path/to/urls.txt

[recon-ng][default][ssl_scan] > options set SOURCE query SELECT DISTINCT (host || ':' || '443') FROM hosts

[recon-ng][default][ssl_scan] > run

[recon-ng][default][ssl_scan] > back
```

- `migrate_ports` recon-ng module

```
[recon-ng][default] > marketplace install recon/ports-hosts/migrate_ports

[recon-ng][default] > modules load recon/ports-hosts/migrate_ports

[recon-ng][default][migrate_ports] > run

[recon-ng][default][migrate_ports] > back
```

---
## References

- [Certificate Transparency (CT) Logs](https://crt.sh)

- [tls.bufferover.run](https://tls.bufferover.run/)

- [SSLMate](https://sslmate.com/ct_search_api/)

- [SSLTest](https://www.ssllabs.com/ssltest/)

- [SSLTools](https://ssltools.com/)
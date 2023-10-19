# 03 - Whois Enumeration

## 3.1 - Manual

`$ whois <domain.com>`

## 3.2 - Amass

### Setup

```
$ go install -v github.com/owasp-amass/amass/v3/...@master && \
sudo cp ~/go/bin/amass /usr/local/bin
```

### Usage

`$ amass intel -whois -d <website.com> -dir whois-output`

## 3.3 - Recon-ng

- **`viewdns_reverse_whois` recon-ng module**

```
[recon-ng][default] > marketplace install recon/companies-domains/viewdns_reverse_whois

[recon-ng][default] > modules load recon/companies-domains/viewdns_reverse_whois

[recon-ng][default][viewdns_reverse_whois] > options set SOURCE <domain.com>

[recon-ng][default][viewdns_reverse_whois] > options set SOURCE query SELECT DISTINCT host FROM hosts WHERE host IS NOT NULL

[recon-ng][default][viewdns_reverse_whois] > run

[recon-ng][default][viewdns_reverse_whois] > back
```

- **`whois_miner` recon-ng module**

```
[recon-ng][default] > marketplace install recon/companies-multi/whois_miner

[recon-ng][default] > modules load recon/companies-multi/whois_miner

[recon-ng][default][whois_miner] > options set SOURCE <domain.com>

[recon-ng][default][whois_miner] > run

[recon-ng][default][whois_miner] > back
```

- **`whois_orgs` recon-ng module**

```
[recon-ng][default] > marketplace install recon/netblocks-companies/whois_orgs

[recon-ng][default] > modules load recon/netblocks-companies/whois_orgs

[recon-ng][default][whois_orgs] > options set SOURCE <domain.com>

[recon-ng][default][whois_orgs] > run

[recon-ng][default][whois_orgs] > back
```

- **`resolve` recon-ng module**

```
[recon-ng][default] > modules load recon/hosts-hosts/resolve

[recon-ng][default][resolve] > options set SOURCE query SELECT DOMAIN FROM DOMAINS

[recon-ng][default][resolve] > run

[recon-ng][default][resolve] > back
```

- **`reverse_resolve` recon-ng module**

```
[recon-ng][default] > modules load recon/netblocks-hosts/reverse_resolve

[recon-ng][default][reverse_resolve] > run
```

---
## References

- [ViewDNS.info](https://viewdns.info)
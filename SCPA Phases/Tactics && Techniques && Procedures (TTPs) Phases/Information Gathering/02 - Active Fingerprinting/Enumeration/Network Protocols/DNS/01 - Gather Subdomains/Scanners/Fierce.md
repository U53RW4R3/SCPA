# Fierce

## Usage

TODO: Provide more coverage of Fierce

### 01 - Fierce Python Version

`$ fierce --domain <domain.com> --dns-servers <nameserver_IP_1>,<nameserver_IP_2>`

`$ fierce --domain <domain.com> --subdomains www dev admin`

`$ fierce --domain <domain.com> --subdomains dev --traverse 10`

`$ fierce --domain <domain.com> --subdomains mail --connect`

`$ fierce --domain <domain.com> --wide`

```
$ fierce --domain <domain.com> | grep Found | tee output.txt

$ fierce --domain <domain.com> --search <domain.com> | tee output.txt

$ fierce --domain <domain.com> --dictionary wordlist.txt | grep Found | tee output.txt
```

- Extract subdomains

`$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' output.txt > subdomains.txt`

- Extract IPs

```
$ awk -F ". " '{print $3}' output.txt | grep -Eo "(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)" | sort -u ip_targets.txt
```

### 02 - Fierce Perl Version

`$ fierce -dns <domain.com>`

`$ fierce -dns <domain.com> -dns-servers <nameserver_IP>

---
## References

- [Fierce](https://github.com/mschwager/fierce)
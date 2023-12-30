# Fierce

## 01 - Fierce Python Version

`$ fierce --domain <domain.com> | grep Found | tee output.txt`

`$ fierce --domain <domain.com> --dictionary wordlist.txt | grep Found | tee output.txt`

- Extract subdomains

`$ awk -F ". " '{print $2}' output.txt > subdomains.txt`

- Extract IPs

`$ awk -F ". " '{print $3}' output.txt | sort -u | tr -d "()" > ips.txt`

## 02 - Fierce Perl Version

`$ fierce -dns <domain.com> -dns-servers <nameserver_IP>
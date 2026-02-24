# Manual

```
$ curl -s https://api.hackertarget.com/dnslookup/?q=<domain.com>
```

## Automated Script

```bash
#!/bin/sh

curl -s https://api.hackertarget.com/dnslookup/?q=$1 > dnslookup
cat dnslookup | grep -v RRSIG | grep -v DNSKEY | grep -v SOA | grep NS > temp
cat -T temp > temp2
cat temp2 | cut -d "I" -f 7 | rev | cut -c 2- | rev
rm temp temp2
```

The syntax command as it follows.

```
$ chmod +x ht_recon.sh <domain>.<tld>
```
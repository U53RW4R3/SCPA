# [[07 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/11 - Gathering IP Addresses/VirusTotal|VirusTotal]]

```
$ curl -s "https://www.virustotal.com/vtapi/v2/domain/report?domain=<domain>.<tld>&apikey=<api_key>" | jq -r '.domain_siblings[]' | sort -uo subdomains.txt
```
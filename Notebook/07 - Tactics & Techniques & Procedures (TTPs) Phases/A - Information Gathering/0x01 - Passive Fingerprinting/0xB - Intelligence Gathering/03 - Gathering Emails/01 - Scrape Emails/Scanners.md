# Scanners

## [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/01 - Gathering URLs/Scanners/theHarvester|theHarvester]]

```
$ theHarvester -l 1500 -d <domain.com | organization_name> -b brave,baidu,bing,duckduckgo,yahoo,linkedin -f output.json

$ theHarvester -l 1500 -d <domain.com | organization_name> -b brave,baidu,bing,bingapi,duckduckgo,yahoo,twitter,linkedin -f output.json
```

## Whatweb

```
$ whatweb -v <URL>
```

## [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x00 - Exploitation/0xC - Password Cracking/Online/Generate Custom Wordlist/CeWL|CeWL]]

```
$ cewl -u <user_agent> -ne --email_file emails.txt http[s]://<IP>
```

## Nuclei

```
$ nuclei -l urls.txt -t ~/nuclei-templates -id email-extractor -o emails-output.txt
```

## Recon-ng

TODO: Convert this to `sn0int`

- `whois_pocs` recon-ng module

```
[recon-ng][default] > marketplace install recon/domains-contacts/whois_pocs

[recon-ng][default] > modules load recon/domains-contacts/whois_pocs

[recon-ng][default][whois_pocs] > options set SOURCE <domain.com>

[recon-ng][default][whois_pocs] > run

[recon-ng][default][whois_pocs] > back
```

## Spiderfoot

```
$ ./sf.py -m sfp_emailformat,sfp_duckduckgo,sfp_grep_app -s <domain.com> -F "Affiliate - Email Address"
```

## Metasploit

```
msf > use auxiliary/gather/search_email_collector

msf auxiliary(gather/search_email_collector) > options

Module options (auxiliary/gather/search_email_collector):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   DOMAIN                          yes       The domain name to locate email addresses for
   OUTFILE                         no        A filename to store the generated email list
   SEARCH_BING    true             yes       Enable Bing as a backend search engine
   SEARCH_GOOGLE  true             yes       Enable Google as a backend search engine
   SEARCH_YAHOO   true             yes       Enable Yahoo! as a backend search engine

msf auxiliary(gather/search_email_collector) > set domain <website.com>

msf auxiliary(gather/search_email_collector) > set search_bing <true | false>

msf auxiliary(gather/search_email_collector) > set search_google <true | false>

msf auxiliary(gather/search_email_collector) > set search_yahoo <true | false>

msf auxiliary(gather/search_email_collector) > set outfile /path/to/file.txt

msf auxiliary(gather/search_email_collector) > run
```

## [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/01 - Gathering URLs/Scanners/Phonebook|Phonebook]]

```
$ phonebook -e <domain>.<tld> -o emails.txt
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/0x02 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents]]

### Hacking Articles

- [Hacking Articles: A Detailed Guide on Cewl](https://www.hackingarticles.in/a-detailed-guide-on-cewl/)
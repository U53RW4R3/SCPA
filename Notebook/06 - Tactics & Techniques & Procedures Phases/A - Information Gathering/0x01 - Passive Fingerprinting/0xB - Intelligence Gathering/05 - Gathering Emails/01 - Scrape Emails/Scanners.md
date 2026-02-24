# Scanners

## Dorking

### #theharvester

```
$ theHarvester -l 1500 -d <domain.tld | organization_name> -b brave,baidu,bing,duckduckgo,yahoo,linkedin -f output.json

$ theHarvester -l 1500 -d <domain.com | organization_name> -b brave,baidu,bing,bingapi,duckduckgo,yahoo,twitter,linkedin -f output.json
```

### #spiderfoot

```
$ ./sf.py -m sfp_emailformat,sfp_duckduckgo,sfp_grep_app -s <domain>.<tld> -F "Affiliate - Email Address"
```

### #metasploit

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

msf auxiliary(gather/search_email_collector) > set outfile /path/to/file.txt

msf auxiliary(gather/search_email_collector) > run domain=<domain>.<tld> search_bing=true search_google=true search_yahoo=true
```

## Web Crawling

### #cewl

```
$ cewl -u <user_agent> -d 8 -ne --email_file emails.txt <URL>
```

Spidering other URLs under the same domain.

```
$ cewl -u <user_agent> -d 8 -one --email_file emails.txt <URL>
```

### #whatweb

```
$ whatweb -v <URL>
```

### #nuclei

```
$ nuclei -l urls.txt -t ~/nuclei-templates -id email-extractor -o emails-output.txt
```

## OSINT

### #gomapenum

```
$ GoMapEnum gather searchEngine -c <organization_name> -f '{first}.{last}@domain.com' -e

$ GoMapEnum gather searchEngine -c <organization_name> -f '{f}.{last}@domain.com' -e

$ GoMapEnum gather searchEngine -c <organization_name> -f "{f}{last}@domain.com" -e

$ GoMapEnum gather searchEngine -c <organization_name> -f '{first}.{l}@domain.com' -e

$ GoMapEnum gather searchEngine -c <organization_name> -f '<DOMAIN>\{first}.{last}' -e
```

### #crosslinked

Basic format.

```
$ crosslinked --proxy-file proxies.txt -f '{first}.{last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{f}.{last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{f}{last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{first}.{l}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '<DOMAIN>\{first}.{last}' -t 15 -j 30 "<organization_name>"
```

Advanced formatting.

```
$ crosslinked --proxy-file proxies.txt -f '{0:first}.{-2:last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{first}.{1:last}@domain.com' -t 15 -j 30 "<organization_name>"
```

### #phonebook

```
$ phonebook -e <domain>.<tld> -o emails.txt
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/D - Webapp Pentesting/0x03 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents|Webapp Pentesting: User Agents]]

### Hacking Articles

- [Hacking Articles: A Detailed Guide on Cewl](https://www.hackingarticles.in/a-detailed-guide-on-cewl/)

- [Hackers Arise: Using QRCodes in Phishing and Social Media Attacks](https://hackers-arise.com/cyberwar-mission-3-turning-your-enemies-strength-against-them/)

- [Hackers Arise: Using QRCodes in Phishing and Social Media Attacks](https://hackers-arise.com/cyberwar-mission-3-turning-your-enemies-strength-against-them-2/)
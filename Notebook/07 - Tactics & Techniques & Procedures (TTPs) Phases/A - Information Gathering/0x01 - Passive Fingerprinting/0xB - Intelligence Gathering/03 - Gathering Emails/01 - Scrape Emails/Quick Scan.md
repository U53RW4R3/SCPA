# Quick Scan

## theHarvester

```
$ theHarvester -l 1500 -d <domain.com | organization_name> -b bing,yahoo,duckduckgo

$ theHarvester -d <domain.com | organization_name> -l 800 -b google,bing,yahoo,duckduckgo,twitter,linkedin,sublist3r,dnsdumpster

$ theHarvester -d DigiNinja -b google,bing,linkedin,duckduckgo -f digininja.xml
```

## Whatweb

```
$ whatweb -v <URL>
```

## CeWL

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

- `pgp_search` recon-ng module

```
[recon-ng][default] > marketplace install recon/domains-contacts/pgp_search

[recon-ng][default] > modules load recon/domains-contacts/pgp_search

[recon-ng][default][pgp_search] > options set SOURCE <domain.com>

[recon-ng][default][pgp_search] > run

[recon-ng][default][pgp_search] > back
```

## Spiderfoot

```
$ ./sf.py -m sfp_emailformat,sfp_pgp,sfp_duckduckgo,sfp_grep_app -s <domain.com> -F "Affiliate - Email Address"
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

---
## References

- [[User Agents]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x00 - Exploitation/0xC - Password Cracking/Online/Generate Custom Wordlist/CeWL|CeWL]]

- [theHarvester](https://github.com/laramies/theHarvester)

- [Hacking Articles: A Detailed Guide on Cewl](https://www.hackingarticles.in/a-detailed-guide-on-cewl/)
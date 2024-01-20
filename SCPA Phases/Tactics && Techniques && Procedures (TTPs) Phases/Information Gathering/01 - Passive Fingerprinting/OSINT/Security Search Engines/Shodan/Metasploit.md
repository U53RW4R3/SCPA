# Metasploit

TODO: Give a step by step approach when using MSF modules

## Shodan search auxiliary module

```
msf > use auxiliary/gather/shodan_search

msf auxiliary(gather/shodan_search) > options

Module options (auxiliary/gather/shodan_search):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   DATABASE       false            no        Add search results to the database
   MAXPAGE        1                yes       Max amount of pages to collect
   OUTFILE                         no        A filename to store the list of IPs
   QUERY                           yes       Keywords you want to search for
   REGEX          .*               yes       Regex search for a specific IP/City/Country/Hostname
   SHODAN_APIKEY                   yes       The SHODAN API key

msf auxiliary(gather/shodan_search) > set shodan_apikey <api>

msf auxiliary(gather/shodan_search) > set database <true | false>

msf auxiliary(gather/shodan_search) > set maxpage <maximum_pages>

msf auxiliary(gather/shodan_search) > set outfile [/path/to/target_ips_output.txt]

msf auxiliary(gather/shodan_search) > set query <shodan_query>

msf auxiliary(gather/shodan_search) > set regex <regex_search>

msf auxiliary(gather/shodan_search) > run
```

## Shodan host auxiliary module

```
msf > use auxiliary/gather/shodan_host

msf auxiliary(gather/shodan_host) > options

Module options (auxiliary/gather/shodan_host):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   Proxies                         no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                          yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   SHODAN_APIKEY                   yes       The SHODAN API key

msf auxiliary(gather/shodan_host) > set shodan_apikey <api>
```

## Shodan honeyscore auxiliary module

```
msf > use auxiliary/gather/shodan_honeyscore

msf auxiliary(gather/shodan_honeyscore) > options

Module options (auxiliary/gather/shodan_honeyscore):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   SHODAN_APIKEY                   yes       The SHODAN API key
   TARGET                          yes       The target to get the score of

msf auxiliary(gather/shodan_honeyscore) > set shodan_apikey <api>
```

---
## References

- [Rapid7: Metasploit Framework Shodan Host Auxiliary Module](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/auxiliary/gather/shodan_host.md)

- [Rapid7: Metasploit Framework Shodan Honeyscore Auxiliary Module](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/auxiliary/gather/shodan_honeyscore.md)
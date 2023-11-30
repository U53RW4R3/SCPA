# 07 - Cloud Lookup

## 7.1 - Metasploit

```
msf > use auxiliary/gather/cloud_lookup

msf auxiliary(gather/cloud_lookup) > set action <Automatic | "Amazon CloudFront" | "ArvanCloud CDN" | AzureCDN | CloudFlare | "Envoy Proxy" | Fastly | "Imperva Incapsula" | "InGen Security (BinarySec EasyWAF)" | KeyCDN | Netlifi | NoWAFBypass | "Stackpath Fireblade" | "Stackpath MaxCDN" | Sucuri>

msf auxiliary(gather/cloud_lookup) > options

Module options (auxiliary/gather/cloud_lookup):

   Name              Current Setting                                              Required  Description
   ----              ---------------                                              --------  -----------
   CENSYS_SECRET                                                                  no        The Censys API SECRET
   CENSYS_UID                                                                     no        The Censys API UID
   COMPSTR                                                                        no        You can use a custom string to perform the comparison (read documentation)
   DOMAIN                                                                         no        The target domain name
   HOSTNAME                                                                       yes       The hostname or domain name where we want to find the real IP address
   IPBLACKLIST_FILE                                                               no        Files containing IP addresses to blacklist during the analysis process, one per line
   NS                                                                             no        Specify the nameservers to use for queries, space separated
   Proxies                                                                        no        A proxy chain of format type:host:port[,type:host:port][...]
   RPORT             443                                                          yes       The target TCP port on which the protected website responds
   SEARCHLIST                                                                     no        DNS domain search list, comma separated
   SSL               true                                                         yes       Negotiate SSL/TLS for outgoing connections
   THREADS           8                                                            yes       Threads for DNS enumeration
   URIPATH           /                                                            yes       The URI path on which to perform the page comparison
   WORDLIST          /usr/share/metasploit-framework/data/wordlists/namelist.txt  no        Wordlist of subdomains


Auxiliary action:

   Name       Description
   ----       -----------
   Automatic



View the full module info with the info, or info -d command.

msf auxiliary(gather/cloud_lookup) > set hostname <www.domain.com>

msf auxiliary(gather/cloud_lookup) > set domain <domain.com>

msf auxiliary(gather/cloud_lookup) > set rport <PORT>

msf auxiliary(gather/cloud_lookup) > set ssl <true | false>

msf auxiliary(gather/cloud_lookup) > set censys_secret <censys_api_secret>

msf auxiliary(gather/cloud_lookup) > set censys_uid <censys_api_uid>

msf auxiliary(gather/cloud_lookup) > set ns <nameserver_IP_1>,<nameserver_IP_2>,<nameserver_IP_n>

msf auxiliary(gather/cloud_lookup) > set ipblacklist_file [/path/to/blacklisted_ips.txt]

msf auxiliary(gather/cloud_lookup) > set uripath </path/to/uri/>

msf auxiliary(gather/cloud_lookup) > set compstr [compare_string]

msf auxiliary(gather/cloud_lookup) > set searchlist <>

msf auxiliary(gather/cloud_lookup) > set wordlist </path/to/slds.txt>

msf auxiliary(gather/cloud_lookup) > set threads 2

msf auxiliary(gather/cloud_lookup) > run
```
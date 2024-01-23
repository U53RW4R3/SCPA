# Metasploit

- Metasploit auxiliary module DNS Amplification Scanner

```
msf > use auxiliary/scanner/dns/dns_amp

msf auxiliary(scanner/dns/dns_amp) > options

Module options (auxiliary/scanner/dns/dns_amp):

   Name        Current Setting  Required  Description
   ----        ---------------  --------  -----------
   BATCHSIZE   256              yes       The number of hosts to probe in each set
   DOMAINNAME  isc.org          yes       Domain to use for the DNS request
   FILTER                       no        The filter string for capturing traffic
   INTERFACE                    no        The name of the interface
   PCAPFILE                     no        The name of the PCAP capture file to process
   QUERYTYPE   ANY              yes       Query type(A, NS, SOA, MX, TXT, AAAA, RRSIG, DNSKEY, ANY)
   RHOSTS                       yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT       53               yes       The target port (UDP)
   SNAPLEN     65535            yes       The number of bytes to capture
   THREADS     10               yes       The number of concurrent threads
   TIMEOUT     500              yes       The number of seconds to wait for new data


View the full module info with the info, or info -d command.

msf auxiliary(scanner/dns/dns_amp) > run threads=8 batchsize=<int> domainname=<domain.com> rhosts=<IP>
```

- Metasploit auxiliary module DNS Record Scanner and Enumerator

```
msf > use auxiliary/gather/enum_dns

msf auxiliary(gather/enum_dns) > options

Module options (auxiliary/gather/enum_dns):

   Name         Current Setting                              Required  Description
   ----         ---------------                              --------  -----------
   DOMAIN                                                    yes       The target domain
   ENUM_A       true                                         yes       Enumerate DNS A record
   ENUM_AXFR    true                                         yes       Initiate a zone transfer against each NS record
   ENUM_BRT     false                                        yes       Brute force subdomains and hostnames via the supplied wordlist
   ENUM_CNAME   true                                         yes       Enumerate DNS CNAME record
   ENUM_MX      true                                         yes       Enumerate DNS MX record
   ENUM_NS      true                                         yes       Enumerate DNS NS record
   ENUM_RVL     false                                        yes       Reverse lookup a range of IP addresses
   ENUM_SOA     true                                         yes       Enumerate DNS SOA record
   ENUM_SRV     true                                         yes       Enumerate the most common SRV records
   ENUM_TLD     false                                        yes       Perform a TLD expansion by replacing the TLD with the IANA TLD list
   ENUM_TXT     true                                         yes       Enumerate DNS TXT record
   IPRANGE                                                   no        The target address range or CIDR identifier
   NS                                                        no        Specify the nameservers to use for queries, space separated
   Proxies                                                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RPORT        53                                           yes       The target port (TCP)
   SEARCHLIST                                                no        DNS domain search list, comma separated
   STOP_WLDCRD  false                                        yes       Stops bruteforce enumeration if wildcard resolution is detected
   THREADS      1                                            no        Threads for ENUM_BRT
   WORDLIST     /opt/metasploit/data/wordlists/namelist.txt  no        Wordlist of subdomains


View the full module info with the info, or info -d command.

msf auxiliary(gather/enum_dns) > run threads=10 [ns=<nameserver_IP_1>,<nameserver_IP_2>,<nameserver_IP_n>] domain=<website.com>
```
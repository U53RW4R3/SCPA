# Scanners

## #amass

```
$ amass enum -brute -d <domain.tld> [-trqps 15] -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt -o subdomains.txt

$ amass enum -active -df domains.txt [-trqps 15] -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt -o subdomains.txt

$ amass db -df domains.txt -names [-trqps 15] -o subdomains.txt
```

## #gobuster

```
$ gobuster dns -d <domain.tld> -t 16 -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt

$ gobuster vhost -d <domain.tld> -t 16 -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt
```

## #dnsrecon

```
$ dnsrecon -d <domain> -t brt --threads 8

$ dnsrecon -d <domain> -t brt --threads 8 -D /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt
```

## #dnsenum

```
$ dnsenum -f /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt <domain.tld>
```

## #fierce

```
$ fierce --domain <domain.tld> --dictionary /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt | grep Found | tee output.txt
```

![[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/01 - Gather Subdomains/Scanners#^4611b2]]

![[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/01 - Gather Subdomains/Scanners#^872a1c]]

![[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/01 - Gather Subdomains/Scanners#^c3b19a]]

![[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/01 - Gather Subdomains/Scanners#^fd49f9]]

## #dnsx

```
$ dnsx -d <domain>.FUZZ -w wordlist.txt -resp

$ for domain in $(cat domains.txt); do dnsx -silent -d FUZZ.$domain -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt -o $domain.txt; done
```

## #wfuzz

```
$ wfuzz -u http[s]://<domain>.<tld> -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt -H "Host: FUZZ.<domain>.<tld>"
```

## #ffuf

```
$ ffuf -u https://FUZZ.domain.tld/ -w /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt -p 1 -f 301,401,403
```

## #knockpy

```
$ knockpy <domain.tld> -t 30 -w subdomains.txt -w SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

## #metasploit

Metasploit auxiliary module DNS Record Scanner and Enumerator

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

msf auxiliary(gather/enum_dns) > set wordlist /usr/share/seclists/Discovery/DNS/subdomains-list-5000.txt

msf auxiliary(gather/enum_dns) > run threads=10 [ns=<nameserver_IP_1>,<nameserver_IP_2>,<nameserver_IP_n>] domain=<website.com>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/10 - Gathering Subdomains/Manual]]

- [[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/02 - Subdomain Bruteforce/Manual]]

### Wordlist

- [Assetnote Wordlists: Best DNS Wordlist](https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt)

### Source Repositories

- [Amass Tutorial](https://github.com/OWASP/Amass/wiki/Tutorial)

- [Amass User Guide](https://github.com/OWASP/Amass/wiki/User-Guide)
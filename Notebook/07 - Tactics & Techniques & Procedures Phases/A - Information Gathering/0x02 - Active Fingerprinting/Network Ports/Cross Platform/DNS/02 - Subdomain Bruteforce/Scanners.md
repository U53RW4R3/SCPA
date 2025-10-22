# Scanners

## Amass

```
$ amass enum -brute -d <website.com> [-trqps 15] -w subdomains-wordlists.txt -o subdomains.txt

$ amass enum -active -df domains.txt [-trqps 15] -w subdomains-wordlists.txt -o subdomains.txt

$ amass db -df domains.txt -names [-trqps 15] -o subdomains.txt
```

## Gobuster

### Setup

```
$ go install github.com/OJ/gobuster/v3@latest && \
sudo mv ~/go/bin/gobuster /usr/local/bin
```

### Help Menu

```
$ gobuster dns -h
Uses DNS subdomain enumeration mode

Usage:
  gobuster dns [flags]

Flags:
  -d, --domain string      The target domain
  -h, --help               help for dns
      --no-fqdn            Do not automatically add a trailing dot to the domain, so the resolver uses the DNS search domain
  -r, --resolver string    Use custom DNS server (format server.com or server.com:port)
  -c, --show-cname         Show CNAME records (cannot be used with '-i' option)
  -i, --show-ips           Show IP addresses
      --timeout duration   DNS resolver timeout (default 1s)
      --wildcard           Force continued operation when wildcard found

Global Flags:
      --debug                 Enable debug output
      --delay duration        Time each thread waits between requests (e.g. 1500ms)
      --no-color              Disable color output
      --no-error              Don't display errors
  -z, --no-progress           Don't display progress
  -o, --output string         Output file to write results to (defaults to stdout)
  -p, --pattern string        File containing replacement patterns
  -q, --quiet                 Don't print the banner and other noise
  -t, --threads int           Number of concurrent threads (default 10)
  -v, --verbose               Verbose output (errors)
  -w, --wordlist string       Path to the wordlist. Set to - to use STDIN.
      --wordlist-offset int   Resume from a given position in the wordlist (defaults to 0)
```

### Usage

```
$ gobuster dns -d <domain.com> -t 16 -w wordlist.txt
```

## DNSRecon

```
$ dnsrecon -d <domain> -t brt --threads 8

$ dnsrecon -d <domain> -t brt --threads 8 -D wordlist.txt
```

## DNSEnum

```

```

## Fierce

```
$ fierce --domain <domain.com> --dictionary wordlist.txt | grep Found | tee output.txt
```

Extract subdomains

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' output.txt > subdomains.txt
```

Extract IPs

```
$ awk -F ". " '{print $3}' output.txt | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" | sort -u > ip_targets.txt
```

## DNSx

```
$ dnsx -d <domain>.FUZZ -w wordlist.txt -resp

$ for domain in $(cat domains.txt); do dnsx -silent -d FUZZ.$domain -w wordlist.txt -o $domain.txt; done
```

## Ffuf

```
$ ffuf -u https://FUZZ.domain.tld/ -w subdomains.txt -p 1 -f 301,401,403
```

## Knockpy

```
$ knockpy domain.tld -t 30 -w subdomains.txt -w SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

## Recon-ng

`brute_hosts` recon-ng module
 
```
[recon-ng][default] > marketplace install recon/domains-hosts/brute_hosts

[recon-ng][default][brute_hosts] > modules load recon/domains-hosts/brute_hosts

[recon-ng][default][brute_hosts] > options set SOURCE <domain.com>

[recon-ng][default][brute_hosts] > run
```

## Metasploit

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

msf auxiliary(gather/enum_dns) > run threads=10 [ns=<nameserver_IP_1>,<nameserver_IP_2>,<nameserver_IP_n>] domain=<website.com>
```

---
## References

### Backlinks

- [[Domains]]

- [[07 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/02 - Subdomain Bruteforce/Manual]]

### Wordlist

- [Assetnote Wordlists: Best DNS Wordlist](https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt)

### Source Repositories

- [Amass Tutorial](https://github.com/OWASP/Amass/wiki/Tutorial)

- [Amass User Guide](https://github.com/OWASP/Amass/wiki/User-Guide)
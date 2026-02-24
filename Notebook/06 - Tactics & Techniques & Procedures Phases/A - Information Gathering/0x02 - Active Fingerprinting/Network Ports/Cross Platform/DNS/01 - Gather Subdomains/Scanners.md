---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - dns
  - network-mapper
---
# Scanners

## #dnsrecon

```
$ dnsrecon -d <domain.tld>
```

## #fierce 

Append a couple of subdomains.

```
$ fierce --domain <domain.tld> --subdomains accounts admin ads dev
```

Specify DNS nameservers to resolve by gathering the subdomains.

```
$ fierce --domain <domain.tld> --dns-servers <nameserver_IP_1>,<nameserver_IP_2>
```

Traverse IPs near discovered domains to search for contiguous blocks.

```
$ fierce --domain <domain.tld> --subdomains dev --traverse 10
```

Perform an attempt of HTTP connection.

```
$ fierce --domain <domain.tld> --subdomains mail --connect
```

Scan to look for nearby domains with a CIDR blocks of `/24`.

```
$ fierce --domain <domain.tld> --wide
```

Specify DNS nameservers especially when dealing with internal networks.

```
$ fierce --range <IP>/<CIDR> --dns-servers <nameserver_IP>
```

You can narrow the search by specifying domains.

```
$ fierce --domain <domain.com> --search <domain.tld_1> <domain.tld_n> | tee output.txt
```

To output the results.

```
$ fierce --domain <domain.com> | grep Found | tee output.txt
```

Extract subdomains from the output. ^4611b2

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' output.txt > subdomains.txt
```

^872a1c

Extract IP addresses from the output. ^c3b19a

```
$ awk -F ". " '{print $3}' output.txt | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" | sort -uo ip_targets.txt
```

^fd49f9

## #theharvester

```
$ theHarvester -n -c -l 1000 -d <domain.tld | organization_name> -b bufferoverun,certspotter,crtsh,dnsdumpster,hackertarget
```

## #knockpy

```
$ knockpy <domain.com>
```

## #network-mapper 

```
$ nmap -p 53 --script dns-zone-transfer --script-args="dns-zone.transfer.domain=<domain.com>" <nameserver_IP>

$ nmap -p 53 --script dns-check-zone --script-args="dns-check-zone.domain=<domain.com>" <IP>

$ sudo nmap -p 53,80,443,8000,8080,8443 -sS --script dns-brute --script-args="dns-brute.domain=<domain.com>,dns-brute.hostlist=subdomains.txt" <IP>
```

If you want to specify a specific dns server to lookup

```
$ nmap -sL --dns-servers <dns_server_1>,<dns_server_2>,<dns_server_n> <IP>/<CIDR>
```

## #metasploit

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

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/DNS/01 - Gather Subdomains/Manual]]
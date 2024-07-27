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
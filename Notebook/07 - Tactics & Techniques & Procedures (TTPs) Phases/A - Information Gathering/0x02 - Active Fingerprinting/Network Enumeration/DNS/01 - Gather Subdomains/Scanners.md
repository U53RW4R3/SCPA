# Scanners

## DNSRecon

```
$ dnsrecon -d <domain.com>
```

## Fierce

TODO: Provide more coverage of Fierce

### 01 - Python Version

```
$ fierce --domain <domain.com> --dns-servers <nameserver_IP_1>,<nameserver_IP_2>
```

```
$ fierce --domain <domain.com> --subdomains www dev admin
```

```
$ fierce --domain <domain.com> --subdomains dev --traverse 10
```

```
$ fierce --domain <domain.com> --subdomains mail --connect
```

```
$ fierce --domain <domain.com> --wide
```

```
$ fierce --domain <domain.com> | grep Found | tee output.txt

$ fierce --domain <domain.com> --search <domain.com> | tee output.txt

$ fierce --domain <domain.com> --dictionary wordlist.txt | grep Found | tee output.txt
```

Extract subdomains via regex statement.

```
$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' output.txt > subdomains.txt
```

Extract IP addresses via regex statement.

```
$ awk -F ". " '{print $3}' output.txt | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | sort -u ip_targets.txt
```

### 02 - Perl Version

```
$ fierce -dns <domain.com>

$ fierce -dns <domain.com> -dns-servers <nameserver_IP>
```

## Recon-ng

TODO: Convert it to `sn0int`

### Resolve URLs with IPs

- `resolve` recon-ng module

```
[recon-ng][default] > modules load recon/hosts-hosts/resolve

[recon-ng][default][resolve] > run
```

### Reverse resolve netblocks

- `reverse_resolve` recon-ng module

```
[recon-ng][default] > modules load recon/netblocks-hosts/reverse_resolve

[recon-ng][default][reverse_resolve] > run
```

## Sublist3r2

### Setup

```
$ git clone https://github.com/RoninNakomoto/Sublist3r2.git && \
python3 -m venv ~/environments/sublist3r2 && \
source ~/environments/sublist3r2/bin/activate && \
python -m pip install --upgrade pip && \
cd ~/sublist3r2/ && pip install -r requirements.txt && \
deactivate
```

### Usage

```
$ source ~/environments/sublist3r2/bin/activate

$ sublist3r2 -d website.com -b -t 64 -o subdomains.txt
```

## Knockpy

```
$ knockpy <domain.com>
```

## Nmap

```
$ nmap -p 53 --script dns-zone-transfer --script-args="dns-zone.transfer.domain=<domain.com>" <nameserver_IP>

$ nmap -p 53 --script dns-check-zone --script-args="dns-check-zone.domain=<domain.com>" <IP>

$ sudo nmap -p 53,80,443,8000,8080,8443 -sS --script dns-brute --script-args="dns-brute.domain=<domain.com>,dns-brute.hostlist=subdomains.txt" <IP>
```

If you want to specify a specific dns server to lookup

```
$ nmap -sL --dns-servers <dns_server_1>,<dns_server_2>,<dns_server_n> <IP>/<CIDR>
```

## Metasploit

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

---
## References

- [Fierce](https://github.com/mschwager/fierce)

- [Knock](https://github.com/guelfoweb/knock)
# Scanners

## CloudRecon

### 01 - Setup

```
$ go install github.com/g0ldencybersec/CloudRecon@latest && \
sudo mv ~/go/bin/CloudRecon /usr/local/bin/
```

### 02 - Help Menu

#### 2.1 - Main Options

```
$ CloudRecon -h
Usage: CloudRecon scrape|store|retr [options]

  -h    Show the program usage message

Subcommands: 

        cloudrecon scrape - Scrape given IPs and output CNs & SANs to stdout
        cloudrecon store - Scrape and collect Orgs,CNs,SANs in local db file
        cloudrecon retr - Query local DB file for results
```

#### 2.2 - Scrape Options

```
$ CloudRecon scrape -h
No input detected, please use the -i flag to add input!

scrape [options] -i <IPs/CIDRs or File>
  -a    Add this flag if you want to see all output including failures
  -c int
        How many goroutines running concurrently (default 100)
  -h    print usage!
  -i string
        Either IPs & CIDRs separated by commas, or a file with IPs/CIDRs on each line (default "NONE")
  -j    Generate JSON output
  -p string
        TLS ports to check for certificates (default "443")
  -t int
        Timeout for TLS handshake (default 4)
```

#### 2.3 - Store Options

```
$ CloudRecon store -h 
No input detected, please use the -i flag to add input!

store [options] -i <IPs/CIDRs or File>
  -c int
        How many goroutines running concurrently (default 100)
  -db string
        String of the DB you want to connect to and save certs! (default "certificates.db")
  -h    print usage!
  -i string
        Either IPs & CIDRs separated by commas, or a file with IPs/CIDRs on each line (default "NONE")
  -p string
        TLS ports to check for certificates (default "443")
  -t int
        Timeout for TLS handshake (default 4)
```

#### 2.4 - Retr Options

```
$ CloudRecon retr -h 
retr [options]
  -all
        Return all the rows in the DB
  -cn string
        String to search for in common name column, returns like-results (default "NONE")
  -db string
        String of the DB you want to connect to and save certs! (default "certificates.db")
  -h    print usage!
  -ip string
        String to search for in IP column, returns like-results (default "NONE")
  -num
        Return the Number of rows (results) in the DB (By IP)
  -org string
        String to search for in Organization column, returns like-results (default "NONE")
  -san string
        String to search for in common name column, returns like-results (default "NONE")
```

### 03 - Usage

TODO: Fill this info

```
$ CloudRecon scrape -i ip_range.txt | tee tls-dns-certificate-output.txt
```

## #sn0int

```
[sn0int][default] > install kpcyrd/tls-san-scan

[sn0int][default] > use kpcyrd/tls-san-scan

[sn0int][default][kpcyrd/tls-san-scan] > run
```

## [[SSLScan|SSLScan]]

Gather subdomains.

```
$ sslscan --show-certificate <target_IP>:443 | tee tls-dns-certificate-output.txt

$ sslscan --show-certificate <URL> | tee tls-dns-certificate-output.txt
```

Then [[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/10 - Gathering Subdomains/Manual|extract them]].

```
$ grep "Altnames:" tls-dns-certificate-output.txt | grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' | sort -u > subdomains-output.txt
```

## [[SSLyze|SSLyze]]

Gather subdomains.

```
$ sslyze --certinfo <IP> | tee tls-dns-certificate-output.txt
```

Then [[06 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/10 - Gathering Subdomains/Manual|extract them]].

```
$ grep "SubjAltName - DNS Names" tls-dns-certificate-output.txt | grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' | sort -u > subdomains-output.txt
```

## #testssl

```
$ testssl --quiet -S -iL ip_targets.txt -oL tls-dns-certificate-output.txt <<< yes

$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' tls-dns-certificate-output.txt | sort -u > subdomains-output.txt
```

## [[TLSx|TLSx]]

```
$ tlsx -l ip_targets.txt -san -o tls-dns-certificates.txt

$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' tls-dns-certificate-output.txt | sort -u > subdomains-output.txt
```

## #nuclei

```
$ nuclei -u <URL> -t ~/nuclei-templates -id ssl-dns-names

$ nuclei -l ip_targets.txt -t ~/nuclei-templates -id ssl-dns-names
```

## #network-mapper

Probe for subdomains.

```
$ nmap -p 443 -Pn --script ssl-cert <IP>
```

^7c92b9

---
## References

### Source Repositories

- [CloudRecon](https://github.com/g0ldencybersec/CloudRecon)
# Subfinder

## Setup

```
$ go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest && \
sudo cp ~/go/bin/subfinder /usr/local/bin
```

## Help Menu

```
$ subfinder -h                               
Subfinder is a subdomain discovery tool that discovers subdomains for websites by using passive online sources.

Usage:
  subfinder [flags]

Flags:
INPUT:
   -d, -domain string[]  domains to find subdomains for
   -dL, -list string     file containing list of domains for subdomain discovery

SOURCE:
   -s, -sources string[]           specific sources to use for discovery (-s crtsh,github). Use -ls to display all available sources.
   -recursive                      use only sources that can handle subdomains recursively (e.g. subdomain.domain.tld vs domain.tld)
   -all                            use all sources for enumeration (slow)
   -es, -exclude-sources string[]  sources to exclude from enumeration (-es alienvault,zoomeye)

FILTER:
   -m, -match string[]   subdomain or list of subdomain to match (file or comma separated)
   -f, -filter string[]   subdomain or list of subdomain to filter (file or comma separated)

RATE-LIMIT:
   -rl, -rate-limit int  maximum number of http requests to send per second
   -t int                number of concurrent goroutines for resolving (-active only) (default 10)

UPDATE:
   -up, -update                 update subfinder to latest version
   -duc, -disable-update-check  disable automatic subfinder update check

OUTPUT:
   -o, -output string       file to write output to
   -oJ, -json               write output in JSONL(ines) format
   -oD, -output-dir string  directory to write output (-dL only)
   -cs, -collect-sources    include all sources in the output (-json only)
   -oI, -ip                 include host IP in output (-active only)

CONFIGURATION:
   -config string                flag config file (default "/home/userware/.config/subfinder/config.yaml")
   -pc, -provider-config string  provider config file (default "/home/userware/.config/subfinder/provider-config.yaml")
   -r string[]                   comma separated list of resolvers to use
   -rL, -rlist string            file containing list of resolvers to use
   -nW, -active                  display active subdomains only
   -proxy string                 http proxy to use with subfinder
   -ei, -exclude-ip              exclude IPs from the list of domains

DEBUG:
   -silent             show only subdomains in output
   -version            show version of subfinder
   -v                  show verbose output
   -nc, -no-color      disable color in output
   -ls, -list-sources  list all available sources
   -stats              report source statistics

OPTIMIZATION:
   -timeout int   seconds to wait before timing out (default 30)
   -max-time int  minutes to wait for enumeration results (default 10)
```

TODO: Fill this info

## Usage

`$ subfinder -d <domain.com>`

`$ subfinder -dL domains.txt`

`$ subfinder -ls`

`$ subfinder -s crtsh,dnsdumpster,hackertarget -dL domains.txt`

## Use Cases

### Active Subdomains

`$ subfinder -silent -dL domains.txt | dnsx -silent -o live-subdomains-output.txt`
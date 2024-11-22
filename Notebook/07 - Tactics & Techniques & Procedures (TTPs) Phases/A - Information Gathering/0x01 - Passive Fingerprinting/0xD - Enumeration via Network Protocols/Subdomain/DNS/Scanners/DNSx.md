# DNSx

## 01 - Setup

```
$ go install github.com/projectdiscovery/dnsx/cmd/dnsx@latest && \
sudo mv ~/go/bin/dnsx /usr/local/bin
```

## 02 - Help Menu

```
$ dnsx -h                          
dnsx is a fast and multi-purpose DNS toolkit allow to run multiple probes using retryabledns library.

Usage:
  dnsx [flags]

Flags:
INPUT:
   -l, -list string      list of sub(domains)/hosts to resolve (file or stdin)
   -d, -domain string    list of domain to bruteforce (file or comma separated or stdin)
   -w, -wordlist string  list of words to bruteforce (file or comma separated or stdin)

QUERY:
   -a      query A record (default)
   -aaaa   query AAAA record
   -cname  query CNAME record
   -ns     query NS record
   -txt    query TXT record
   -srv    query SRV record
   -ptr    query PTR record
   -mx     query MX record
   -soa    query SOA record
   -axfr   query AXFR
   -caa    query CAA record

FILTER:
   -re, -resp          display dns response
   -ro, -resp-only     display dns response only
   -rc, -rcode string  filter result by dns status code (eg. -rcode noerror,servfail,refused)

PROBE:
   -cdn  display cdn name
   -asn  display host asn information

RATE-LIMIT:
   -t, -threads int      number of concurrent threads to use (default 100)
   -rl, -rate-limit int  number of dns request/second to make (disabled as default) (default -1)

UPDATE:
   -up, -update                 update dnsx to latest version
   -duc, -disable-update-check  disable automatic dnsx update check

OUTPUT:
   -o, -output string  file to write output
   -json               write output in JSONL(ines) format

DEBUG:
   -hc, -health-check  run diagnostic check up
   -silent             display only results in the output
   -v, -verbose        display verbose output
   -raw, -debug        display raw dns response
   -stats              display stats of the running scan
   -version            display version of dnsx

OPTIMIZATION:
   -retry int                number of dns attempts to make (must be at least 1) (default 2)
   -hf, -hostsfile           use system host file
   -trace                    perform dns tracing
   -trace-max-recursion int  Max recursion for dns trace (default 32767)
   -resume                   resume existing scan
   -stream                   stream mode (wordlist, wildcard, stats and stop/resume will be disabled)

CONFIGURATIONS:
   -r, -resolver string          list of resolvers to use (file or comma separated)
   -wt, -wildcard-threshold int  wildcard filter threshold (default 5)
   -wd, -wildcard-domain string  domain name for wildcard filtering (other flags will be ignored - only json output is supported)
```

## 03 - Usage

TODO: Provide more coverage about `dnsx`

```
$ echo <domain>.<tld> | dnsx

$ dnsx -l subdomains.txt -o live-subdomains-output.txt
```

## 04 - Use Cases

TODO: Provide use cases related to `dnsx`
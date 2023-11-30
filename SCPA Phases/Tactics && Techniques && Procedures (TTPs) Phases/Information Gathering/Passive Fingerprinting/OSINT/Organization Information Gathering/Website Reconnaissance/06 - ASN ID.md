# 06 - ASN ID

## 6.1 - ASNmap

### Setup

```
$ go install github.com/projectdiscovery/asnmap/cmd/asnmap@latest && \
sudo cp ~/go/bin/asnmap /usr/local/bin/
```

### Help Menu

```
$ asnmap -h
Usage:
  ./asnmap [flags]

Flags:
INPUT:
   -a, -asn string[]     target asn to lookup, example: -a AS5650
   -i, -ip string[]      target ip to lookup, example: -i 100.19.12.21, -i 2a10:ad40::
   -d, -domain string[]  target domain to lookup, example: -d google.com, -d facebook.com
   -org string[]         target organization to lookup, example: -org GOOGLE
   -f, -file string[]    targets to lookup from file

CONFIGURATIONS:
   -config string           path to the asnmap configuration file
   -r, -resolvers string[]  list of resolvers to use

OUTPUT:
   -o, -output string  file to write output to
   -j, -json           display json format output
   -c, -csv            display csv format output
   -v6                 display ipv6 cidr ranges in cli output
   -v, -verbose        display verbose output
   -silent             display silent output
   -version            show version of the project
```

### Usage

- Lookup target via ASN

`$ asnmap -a <asn_ID_1>,<asn_ID_2>,<asn_ID_n> -o output.txt`

- Lookup target via IP

`$ asnmap -i <IP_1>,<IP_2>,<IP_n> -o output.txt`

- Lookup target via domain

`$ asnmap -d <domain_1>,<domain_2>,<domain_n> -o output.txt`

- Lookup target via organization

`$ asnmap -org <organization_1>,<organization_2>,<organization_n> -o output.txt`

- Lookup targets list

`$ asnmap -f targets.txt -o output.txt`

## 6.2 - Amass

`$ amass intel -active -asn <ASN_ID>`

## 6.3 - Metasploit

```
msf > use auxiliary/gather/corpwatch_lookup_name

msf auxiliary(gather/corpwatch_lookup_name) > options

Module options (auxiliary/gather/corpwatch_lookup_name):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   COMPANY_NAME                       yes       Search for companies with this name
   CORPWATCH_APIKEY                   no        Use this API key when getting the data
   LIMIT             5                yes       Limit the number of results returned
   YEAR              2021             no        Year to look up

msf auxiliary(gather/corpwatch_lookup_name) > set company_name <organization_name>

msf auxiliary(gather/corpwatch_lookup_name) > set limit <int>

msf auxiliary(gather/corpwatch_lookup_name) > run
```
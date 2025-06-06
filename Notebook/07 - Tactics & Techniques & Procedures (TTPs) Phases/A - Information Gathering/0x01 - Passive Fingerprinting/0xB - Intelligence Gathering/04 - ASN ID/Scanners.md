# Scanners

## theHarvester

> [!TIP] Anonymize Your Recon
> You can use TOR or any anonymization networking protocol with the `theHarvester` to retrieve ASN ID.

```
$ theHarvester -d domain.tld -b urlscan
```

## sn0int

```
[sn0int][default] > install kpcyrd/asn

[sn0int][default] > use kpcyrd/asn

[sn0int][default][kpcyrd/asn] > run
```

## Amass

```
$ amass intel -d <domain.com>

$ amass intel -org '<organization_name>'

$ amass intel -active -asn <asn_ID> [-trqps 15] -ip -o output.txt
```

## ASNmap

### Setup

```
$ go install github.com/projectdiscovery/asnmap/cmd/asnmap@latest && \
sudo mv ~/go/bin/asnmap /usr/local/bin/
```

### Usage

Lookup target via ASN

```
$ asnmap -a <asn_ID_1>,<asn_ID_2>,<asn_ID_n> -o output.txt
```

Lookup target via IP

```
$ asnmap -i <IP_1>,<IP_2>,<IP_n> -o output.txt
```

Lookup target via domain

```
$ asnmap -d <domain_1>,<domain_2>,<domain_n> -o output.txt
```

Lookup target via organization

```
$ asnmap -org <organization_1>,<organization_2>,<organization_n> -o output.txt
```

Lookup targets list

```
$ asnmap -f targets.txt -o output.txt
```

## Network Mapper

### Gather IP addresses via ASN ID

```
$ nmap --script targets-asn --script-args targets-asn.asn=<asn_ID>
```

### Query ASN DNS Server

```
$ nmap --script asn-query [--script-args dns=<dns_server_IP>] <IP>
```
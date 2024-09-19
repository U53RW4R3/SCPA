# Network Mapper

Search Tag(s): #information-gathering #passive-reconnaissance #network-protocols #network-mapper

## Gather IP addresses via ASN ID

```
$ nmap --script targets-asn --script-args targets-asn.asn=<asn_ID>
```

## Query ASN DNS Server

```
$ nmap --script asn-query [--script-args dns=<dns_server_IP>] <IP>
```
# Nmap

```
$ nmap -p 53 --script dns-zone-transfer --script-args="dns-zone.transfer.domain=<domain.com>" <nameserver_IP>

$ nmap -p 53 --script dns-check-zone --script-args="dns-check-zone.domain=<domain.com>" <IP>

$ sudo nmap -p 53,80,443 -sS --script dns-brute --script-args="dns-brute.domain=<domain.com>,dns-brute.hostlist=subdomains.txt" <IP>
```

- If you want to specify a specific dns server to lookup

`$ nmap -sL --dns-servers <dns_server_1>,<dns_server_2>,<dns_server_n> <IP>/<CIDR>`
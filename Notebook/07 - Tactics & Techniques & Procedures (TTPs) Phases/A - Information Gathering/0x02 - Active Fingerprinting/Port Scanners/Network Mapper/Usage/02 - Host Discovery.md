---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - network-mapper
---
# 02 - Host Discovery

## 2.1 - IP Range and List

Range of IP targets to scan.

```
$ nmap 192.168.0.23-110
```

List of IP targets to scan.

```
$ nmap 192.168.0.23,110,166
```

List of IP targets in a text file

```
$ nmap -iL targets.txt
```

Network Mapper can check which hosts to scan without scanning them

```
$ nmap -sL <IP>/<CIDR>

$ nmap -sL 192.168.1.0/24
```

## 2.2 - ICMP Scan

Ping Sweep

```
$ sudo nmap -sn <IP>/<CIDR>

$ nmap -sn -T4 <IP>/<CIDR> -oG - | awk '/Up$/{print $2}'
```

Echo Scan

```
$ sudo nmap -PE -sn <IP>/<CIDR>
```

Timestamp Scan

```
$ sudo nmap -PP -sn <IP>/<CIDR>
```

Address Mask Scan

```
$ sudo nmap -PM -sn <IP>/<CIDR>
```

## 2.3 - ARP Scan

```
$ sudo nmap -PR -sn <IP>/<CIDR>
```

## 2.4 - TCP Scan

TCP SYN Ping Scan

```
$ sudo nmap -sn -PS 22,80,443 <IP>/<CIDR>
```

TCP ACK Ping Scan

```
$ sudo nmap -sn -PA 22,80,443 <IP>/<CIDR>
```

## 2.5 - UDP Scan

```
$ sudo nmap -sn -PU53,88,161,162 <IP>/<CIDR>
```

## 2.6 - DNS Lookup

No Reverse-DNS Lookup

```
$ nmap -n <IP>/<CIDR>
```

Reverse-DNS lookup

```
$ nmap -R --dns-servers <dns_nameserver_IP> <IP>/<CIDR>
```

## 2.7 - Traceroute

```
$ sudo nmap --traceroute -sn -PE <IP>
```

## 2.8 - Resolve IP Addresses

TODO: Test this NSE script

```
$ nmap --resolve-all <IP>

$ nmap --script resolveall --script-args=newtargets,resolveall.hosts={<host1>, ...} <IP>
```

## 2.9 - ICMP Forwarding Enabled

```
$ sudo nmap -sn --script ip-forwarding --script-args='target=<website.com>' <IP>
```

## 2.10 - Ignore TCP Reset (RST) Replies

Sometimes firewalls will spoof the scanner with TCP reset replies as proof that the host is online. Specifying this flag will speed up the scanning process.

```
$ nmap --discovery-ignore-rst <IP>/<CIDR>
```

---
## References

### Network Mapper

- [Network Mapper NSEDocs: resolveall Script](https://nmap.org/nsedoc/scripts/resolveall.html)

### Ethical hacking and penetration testing

- [Ethical hacking and penetration testing: Network Mapper usage tips](https://miloserdov.org/?p=3639)
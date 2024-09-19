# 03 - Host Discovery

Search Tags(s): #active-reconnaissance #port-scanners #network-mapper

## 3.1 - IP Range and List

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

## 3.2 - ICMP Scan

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

## 3.3 - ARP Scan

```
$ sudo nmap -PR -sn <IP>/<CIDR>
```

## 3.4 - TCP Scan

TCP SYN Ping Scan

```
$ sudo nmap -sn -PS 22,80,443 <IP>/<CIDR>
```

TCP ACK Ping Scan

```
$ sudo nmap -sn -PA 22,80,443 <IP>/<CIDR>
```

## 3.5 - UDP Scan

```
$ sudo nmap -sn -PU53,88,161,162 <IP>/<CIDR>
```

## 3.6 - DNS Lookup

No Reverse-DNS Lookup

```
$ nmap -n <IP>/<CIDR>
```

Reverse-DNS lookup

```
$ nmap -R <IP>/<CIDR>
```

## 3.7 - Traceroute

```
$ sudo nmap --traceroute -sn -PE <IP>
```

## 3.8 - Resolve IP Addresses

TODO: Test this NSE script

```
$ nmap --resolve-all <IP>

$ nmap --script resolveall --script-args=newtargets,resolveall.hosts={<host1>, ...} <IP>
```

## 3.9 - ICMP Forwarding Enabled

```
$ sudo nmap -sn --script ip-forwarding --script-args='target=<website.com>' <IP>
```

---
## References

- [Network Mapper usage tips](https://miloserdov.org/?p=3639)

- [Network Mapper NSEDocs: Script resolveall](https://nmap.org/nsedoc/scripts/resolveall.html)
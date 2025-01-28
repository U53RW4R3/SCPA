# 08 - Evasion

Search Tags(s): #active-reconnaissance #port-scanners #network-mapper

## 8.1 - Bypass Firewalls and IDS

### 8.1.1 - Disable ICMP and ARP

Disable ICMP scans to ensure the target is online.

```
$ nmap -Pn <IP>
```

Disable ARP pings.

```
$ nmap --disable-arp-ping <IP>
```

### 8.1.2 - Forge Packets

Fragment Packets

```
$ sudo nmap -f <IP>

$ sudo nmap --mtu 8 <IP>
```

Customize Packets

```
$ nmap --data <hex> <IP>

$ nmap --data 0xdeefbeef <IP>

$ nmap --data-string "<string>" <IP>

$ nmap --data-string "Scan conducted by Security Ops, extension 7192" <IP>
```

Send length of arbitrary data

```
$ nmap --data-length <int> <IP>
```

No random data

```
$ nmap --data-length 0 <IP>
```

Send randomized data

```
$ nmap --data-length 5 <IP>
```

Send forged packets

```
$ nmap --badsum <IP>
```

### 8.1.3 -  Spoofing

#### 8.1.3.1 - Decoys

Using SOCKS proxies to disguise ourselves.

```
$ nmap --proxies <schema>://<IP>:<PORT> <target_IP>

$ nmap --proxies socks4://<IP>:<PORT>,http://<IP>:<PORT> <target_IP>
```

Send decoys to the target IP.

```
$ sudo nmap -D <IP_1>,<IP_2>,<IP_3> <target_IP>

$ sudo nmap -D RND:<int> <IP>

$ sudo nmap -D RND:10 <IP>
```

Specify the network interface.

```
$ sudo nmap -e <interface> <IP>
```

Spoof source IP address

```
$ sudo nmap -e <interface> -Pn -S <source_IP> <target_IP>
```

Exploit misconfigured firewall rules with a source port

```
$ sudo nmap -g <PORT> <IP>
```

#### 8.1.3.2 - Idle Zombie Scan

^72346e

Scan for incremental ports to probe

```
$ sudo nmap --script ipidseq [--script-args probeport=<PORT>] <target_IP>
```

Scan a target with a zombie source IP

```
$ sudo nmap -sI <zombie_IP> <target_IP>
```

### 8.1.4 -  FTP Bounce

Using a FTP server as a proxy server to scan the target

```
$ nmap -b <username>:<password>@<FTP_server_IP> <target_IP>

$ nmap -v -p 21,22,80,443,445 -Pn -b <username>:<password>@<FTP_server_IP> <target_IP>/<CIDR>
```

### 8.1.5 -  NSE Script

```
$ sudo nmap --script firewall-bypass --script-args firewall-bypass.helper="ftp",firewall-bypass.targetport=<PORT> <target_IP>
```

## 8.2 - Spoof User Agent

```
$ sudo nmap -p 80,443 -Pn -n -sC --script-args http.useragent="<user_agent>" <IP>
```

## 8.3 - Timing and Performance

### 8.3.1 - Time Intervals

```
$ nmap -T<0-5> <IP>
```

### 8.3.2 -  Rate Limit

```
$ nmap --host-timeout 10ms <IP>

$ nmap --max-retries <0-5> <IP>

$ nmap -sn --min-hostgroup 96 --max-hostgroup 256 <IP>/<CIDR>

$ nmap --scan-delay 11s <IP>

$ nmap --min-rate 2 --max-rate 2 <IP>

$ nmap --min-parallelism 2 --max-parallelism 2 <IP>

$ nmap --min-rtt-timeout 5ms --max-rtt-timeout 50ms <IP>

$ nmap --initial-rtt-timeout 50ms <IP>
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/D - Webapp Pentesting/0x02 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents]]

### Network Mapper

- [Network Mapper: Bypass Firewalls and IDS](https://nmap.org/book/man-bypass-firewalls-ids.html)

### Hacktricks

- [Hacktricks: FTP Bounce Attack](https://book.hacktricks.xyz/pentesting/pentesting-ftp/ftp-bounce-attack)

- [Top 10 Firewall and IDS Evasion Techniques](https://medium.com/@IamLucif3r/top-10-firewall-ids-evasion-techniques-cb1e1cc06f24)

- [Network Mapper Firewall Evasion Techniques](https://www.dimz-it.com/berkas/Nmap_Firewall_Evasion_Techniques.pdf)

- [Firewall Bypassing Techniques with Nmap and Hping3](https://dzone.com/articles/firewall-bypassing-techniques-with-nmap-and-hping3)

### Ethical hacking and penetration testing

- [Ethical hacking and penetration testing: Network Mapper usage tips](https://miloserdov.org/?p=3639)
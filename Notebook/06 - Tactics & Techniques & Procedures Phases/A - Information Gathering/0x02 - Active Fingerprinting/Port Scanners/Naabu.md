---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - naabu
  - network-mapper
---
# Naabu

## 02 - Help Menu

```
$ naabu -h
Naabu is a port scanning tool written in Go that allows you to enumerate open ports for hosts in a fast and reliable manner.

Usage:
  naabu [flags]

PORT:
   -port, -p string            ports to scan (80,443, 100-200)
   -top-ports, -tp string      top ports to scan (default 100) [full,100,1000]
   -exclude-ports, -ep string  ports to exclude from scan (comma-separated)
   -ports-file, -pf string     list of ports to scan (file)
   -port-threshold, -pts int   port threshold to skip port scan for the host
   -exclude-cdn, -ec           skip full port scans for CDN's (only checks for 80,443)
   -display-cdn, -cdn          display cdn in use

RATE-LIMIT:
   -c int     general internal worker threads (default 25)
   -rate int  packets to send per second (default 1000)

CONFIGURATION:
   -scan-all-ips, -sa                  scan all the IP's associated with DNS record
   -ip-version, -iv string[]           ip version to scan of hostname (4,6) - (default 4)
   -scan-type, -s string               type of port scan (SYN/CONNECT) (default "s")
   -source-ip string                   source ip and port (x.x.x.x:yyy)
   -interface-list, -il                list available interfaces and public ip
   -interface, -i string               network Interface to use for port scan

   -r string                           list of custom resolver dns resolution (comma separated or from file)
   -proxy string                       socks5 proxy (ip[:port] / fqdn[:port]
   -proxy-auth string                  socks5 proxy authentication (username:password)
   -resume                             resume scan using resume.cfg
   -stream                             stream mode (disables resume, nmap, verify, retries, shuffling, etc)
   -passive                            display passive open ports using shodan internetdb api
   -irt, -input-read-timeout duration  timeout on input read (default 3m0s)
   -no-stdin                           Disable Stdin processing

SERVICES-DISCOVERY:
   -sD, -service-discovery  Service Discovery
   -sV, -service-version    Service Version

OPTIMIZATION:
   -retries int       number of retries for the port scan (default 3)
   -timeout int       millisecond to wait before timing out (default 1000)
   -warm-up-time int  time in seconds between scan phases (default 2)
   -ping              ping probes for verification of host
   -verify            validate the ports again with TCP verification
```

## 03 - Usage

```
$ naabu -host <IP> -o port-scanned-output.txt

$ naabu -list ip_targets.txt -o port-scanned-output.txt
```

```
INPUT:
   -exclude-hosts, -eh string  hosts to exclude from the scan (comma-separated)
   -exclude-file, -ef string   list of hosts to exclude from scan (file)
```

```
$ naabu -host <IP> -nmap-cli 'nmap -sC -oA initial'
```

```
   -proxy string                       socks5 proxy (ip[:port] / fqdn[:port]
   -proxy-auth string                  socks5 proxy authentication (username:password)
```

## Use Cases

```
$ naabu -p 80,443 <<< <ASN_ID>
```
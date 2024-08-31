# Naabu

## 01 - Setup

```
$ go install github.com/projectdiscovery/naabu/v2/cmd/naabu@latest && \
sudo mv ~/go/bin/naabu /usr/local/bin
```

## 02 - Help Menu

```
$ naabu -h
Naabu is a port scanning tool written in Go that allows you to enumerate open ports for hosts in a fast and reliable manner.

Usage:
  naabu [flags]

Flags:
INPUT:
   -host string[]              hosts to scan ports for (comma-separated)
   -list, -l string            list of hosts to scan ports (file)
   -exclude-hosts, -eh string  hosts to exclude from the scan (comma-separated)
   -exclude-file, -ef string   list of hosts to exclude from scan (file)

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

UPDATE:
   -up, -update                 update naabu to latest version
   -duc, -disable-update-check  disable automatic naabu update check

OUTPUT:
   -o, -output string  file to write output to (optional)
   -json               write output in JSON lines format
   -csv                write output in csv format

CONFIGURATION:
   -scan-all-ips, -sa                  scan all the IP's associated with DNS record
   -ip-version, -iv string[]           ip version to scan of hostname (4,6) - (default 4)
   -scan-type, -s string               type of port scan (SYN/CONNECT) (default "s")
   -source-ip string                   source ip and port (x.x.x.x:yyy)
   -interface-list, -il                list available interfaces and public ip
   -interface, -i string               network Interface to use for port scan
   -nmap                               invoke nmap scan on targets (nmap must be installed) - Deprecated
   -nmap-cli string                    nmap command to run on found results (example: -nmap-cli 'nmap -sV')
   -r string                           list of custom resolver dns resolution (comma separated or from file)
   -proxy string                       socks5 proxy (ip[:port] / fqdn[:port]
   -proxy-auth string                  socks5 proxy authentication (username:password)
   -resume                             resume scan using resume.cfg
   -stream                             stream mode (disables resume, nmap, verify, retries, shuffling, etc)
   -passive                            display passive open ports using shodan internetdb api
   -irt, -input-read-timeout duration  timeout on input read (default 3m0s)
   -no-stdin                           Disable Stdin processing

HOST-DISCOVERY:
   -sn, -host-discovery           Perform Only Host Discovery
   -Pn, -skip-host-discovery      Skip Host discovery
   -ps, -probe-tcp-syn string[]   TCP SYN Ping (host discovery needs to be enabled)
   -pa, -probe-tcp-ack string[]   TCP ACK Ping (host discovery needs to be enabled)
   -pe, -probe-icmp-echo          ICMP echo request Ping (host discovery needs to be enabled)
   -pp, -probe-icmp-timestamp     ICMP timestamp request Ping (host discovery needs to be enabled)
   -pm, -probe-icmp-address-mask  ICMP address mask request Ping (host discovery needs to be enabled)
   -arp, -arp-ping                ARP ping (host discovery needs to be enabled)
   -nd, -nd-ping                  IPv6 Neighbor Discovery (host discovery needs to be enabled)
   -rev-ptr                       Reverse PTR lookup for input ips

SERVICES-DISCOVERY:
   -sD, -service-discovery  Service Discovery
   -sV, -service-version    Service Version

OPTIMIZATION:
   -retries int       number of retries for the port scan (default 3)
   -timeout int       millisecond to wait before timing out (default 1000)
   -warm-up-time int  time in seconds between scan phases (default 2)
   -ping              ping probes for verification of host
   -verify            validate the ports again with TCP verification

DEBUG:
   -health-check, -hc        run diagnostic check up
   -debug                    display debugging information
   -verbose, -v              display verbose output
   -no-color, -nc            disable colors in CLI output
   -silent                   display only results in output
   -version                  display version of naabu
   -stats                    display stats of the running scan (deprecated)
   -si, -stats-interval int  number of seconds to wait between showing a statistics update (deprecated) (default 5)
   -mp, -metrics-port int    port to expose nuclei metrics on (default 63636)
```

## 03 - Usage

```
$ naabu -host <IP> -o port-scanned-output.txt

$ naabu -list ip_targets.txt -o port-scanned-output.txt

$ echo <ASN_ID> | naabu -p80,443

$ naabu -host <IP> -nmap-cli 'nmap -sC -oA initial'
```

## 04 - Troubleshoot

If you encounter an installation problem for pcap. It's missing some dependencies.

```
github.com/google/gopacket/pcap
# github.com/google/gopacket/pcap
go/pkg/mod/github.com/google/gopacket@v1.1.19/pcap/pcap_unix.go:34:10: fatal error: pcap.h: No such file or directory
   34 | #include <pcap.h>
      |          ^~~~~~~~
compilation terminated.
```

Install this package and the issue should be resolved.

```
$ sudo apt install libpcap-dev
```

---
## References

- [InfoSecWarrior: Offensive Pentesting Host - Naabu](https://github.com/InfoSecWarrior/Offensive-Pentesting-Host/blob/main/Network%20Scanning/NAABU.md)
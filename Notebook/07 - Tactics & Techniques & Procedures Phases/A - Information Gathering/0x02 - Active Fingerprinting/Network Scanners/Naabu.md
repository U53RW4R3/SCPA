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

## 01 - Setup

Run this as root.

```
# go install github.com/projectdiscovery/naabu/v2/cmd/naabu@latest && \
mv ~/go/bin/naabu /usr/local/bin
```

## 02 - Usage

```
HOST-DISCOVERY:
   -sn, -host-discovery           Perform Only Host Discovery
   -Pn, -skip-host-discovery      Skip Host discovery (Deprecated: use -wn/-with-host-discovery instead)
   -wn, -with-host-discovery      Enable Host discovery
   -ps, -probe-tcp-syn string[]   TCP SYN Ping (host discovery needs to be enabled)
   -pa, -probe-tcp-ack string[]   TCP ACK Ping (host discovery needs to be enabled)
   -pe, -probe-icmp-echo          ICMP echo request Ping (host discovery needs to be enabled)
   -pp, -probe-icmp-timestamp     ICMP timestamp request Ping (host discovery needs to be enabled)
   -pm, -probe-icmp-address-mask  ICMP address mask request Ping (host discovery needs to be enabled)
   -arp, -arp-ping                ARP ping (host discovery needs to be enabled)
   -nd, -nd-ping                  IPv6 Neighbor Discovery (host discovery needs to be enabled)
   -rev-ptr                       Reverse PTR lookup for input ips
```

Update `naabu`.

```
# naabu -up
```

```
# naabu -host <IP>/<CIDR> -sn

# naabu -list ip_targets.txt -sn
```

## 03 - Troubleshooting

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
$ sudo apt install -y libpcap-dev
```

---
## References

### InfoSecWarrior

- [InfoSecWarrior: Offensive Pentesting Host - Naabu](https://github.com/InfoSecWarrior/Offensive-Pentesting-Host/blob/main/Network%20Scanning/NAABU.md)
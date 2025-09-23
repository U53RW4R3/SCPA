---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - metasploit-framework
---
# Metasploit

## 01 - Port Scanner Types

### 1.1 - TCP Connect

```
msf > use auxiliary/scanner/portscan/tcp

msf auxiliary(scanner/portscan/tcp) > options

Module options (auxiliary/scanner/portscan/tcp):

   Name         Current Setting  Required  Description
   ----         ---------------  --------  -----------
   CONCURRENCY  10               yes       The number of concurrent ports to check per host
   DELAY        0                yes       The delay between connections, per thread, in milliseconds
   JITTER       0                yes       The delay jitter factor (maximum value by which to +/- DELAY) in milliseconds.
   PORTS        1-10000          yes       Ports to scan (e.g. 22-25,80,110-900)
   RHOSTS                        yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   THREADS      1                yes       The number of concurrent threads (max one per host)
   TIMEOUT      1000             yes       The socket connect timeout in milliseconds


View the full module info with the info, or info -d command.

msf auxiliary(scanner/portscan/tcp) > set rhosts <IP>

msf auxiliary(scanner/portscan/tcp) > set threads <int>

msf auxiliary(scanner/portscan/tcp) > set delay <milliseconds>

msf auxiliary(scanner/portscan/tcp) > set jitter <int>

msf auxiliary(scanner/portscan/tcp) > run
```

^7ae5a4

### 1.2 - TCP ACK Firewall Scanner

```
msf > use auxiliary/scanner/portscan/ack

msf auxiliary(scanner/portscan/ack) > options

Module options (auxiliary/scanner/portscan/ack):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to scan per set
   DELAY      0                yes       The delay between connections, per thread, in milliseconds
   INTERFACE                   no        The name of the interface
   JITTER     0                yes       The delay jitter factor (maximum value by which to +/- DELAY) in milliseconds.
   PORTS      1-10000          yes       Ports to scan (e.g. 22-25,80,110-900)
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   SNAPLEN    65535            yes       The number of bytes to capture
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    500              yes       The reply read timeout in milliseconds


View the full module info with the info, or info -d command.

msf auxiliary(scanner/portscan/ack) > set rhosts <IP>

msf auxiliary(scanner/portscan/ack) > set threads <int>

msf auxiliary(scanner/portscan/ack) > set delay <milliseconds>

msf auxiliary(scanner/portscan/ack) > set jitter <int>

msf auxiliary(scanner/portscan/ack) > run
```

^def6fd

### 1.3 - TCP SYN

^9f5c8c

```
msf > use auxiliary/scanner/portscan/syn

msf auxiliary(scanner/portscan/syn) > options

Module options (auxiliary/scanner/portscan/syn):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to scan per set
   DELAY      0                yes       The delay between connections, per thread, in milliseconds
   INTERFACE                   no        The name of the interface
   JITTER     0                yes       The delay jitter factor (maximum value by which to +/- DELAY) in milliseconds.
   PORTS      1-10000          yes       Ports to scan (e.g. 22-25,80,110-900)
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   SNAPLEN    65535            yes       The number of bytes to capture
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    500              yes       The reply read timeout in milliseconds


View the full module info with the info, or info -d command.

msf auxiliary(scanner/portscan/syn) > set rhosts <IP>

msf auxiliary(scanner/portscan/syn) > set threads <int>

msf auxiliary(scanner/portscan/syn) > set delay <milliseconds>

msf auxiliary(scanner/portscan/syn) > set jitter <int>

msf auxiliary(scanner/portscan/syn) > run
```

^0ff76c

### 1.4 - Xmas Scan

```
msf > use auxiliary/scanner/portscan/xmas

msf auxiliary(scanner/portscan/xmas) > options 

Module options (auxiliary/scanner/portscan/xmas):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to scan per set
   DELAY      0                yes       The delay between connections, per thread, in milliseconds
   INTERFACE                   no        The name of the interface
   JITTER     0                yes       The delay jitter factor (maximum value by which to +/- DELAY) in milliseconds.
   PORTS      1-10000          yes       Ports to scan (e.g. 22-25,80,110-900)
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   SNAPLEN    65535            yes       The number of bytes to capture
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    500              yes       The reply read timeout in milliseconds


View the full module info with the info, or info -d command.

msf auxiliary(scanner/portscan/xmas) > set rhosts <IP>

msf auxiliary(scanner/portscan/xmas) > set threads <int>

msf auxiliary(scanner/portscan/xmas) > set delay <milliseconds>

msf auxiliary(scanner/portscan/xmas) > set jitter <int>

msf auxiliary(scanner/portscan/xmas) > run
```

### 1.5 - UDP Amplification Scanner

```
msf > use auxiliary/scanner/udp/udp_amplification

msf auxiliary(scanner/udp/udp_amplification) > options

Module options (auxiliary/scanner/udp/udp_amplification):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to probe in each set
   PORTS                       yes       Ports to probe
   PROBE                       no        UDP payload/probe to send.  Unset for an empty UDP datagram, or the `file://` resource to get content from a local file
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   THREADS    10               yes       The number of concurrent threads


View the full module info with the info, or info -d command.

msf auxiliary(scanner/udp/udp_amplification) >
```

### 1.6 - Portmapper Amplification Scanner

```
msf > use auxiliary/scanner/portmap/portmap_amp

msf auxiliary(scanner/portmap/portmap_amp) > options

Module options (auxiliary/scanner/portmap/portmap_amp):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to probe in each set
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT      111              yes       The target port (UDP)
   THREADS    10               yes       The number of concurrent threads


View the full module info with the info, or info -d command.

msf auxiliary(scanner/portmap/portmap_amp) >
```

## 02 - Evasion

### 2.1 - Idle Zombie Scan

```
msf > use auxiliary/scanner/ip/ipidseq

msf auxiliary(scanner/ip/ipidseq) > options

Module options (auxiliary/scanner/ip/ipidseq):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   INTERFACE                   no        The name of the interface
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      80               yes       The target port
   SNAPLEN    65535            yes       The number of bytes to capture
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    500              yes       The reply read timeout in milliseconds

msf auxiliary(scanner/ip/ipidseq) > set rhosts <IP>/<CIDR>

msf auxiliary(scanner/ip/ipidseq) > set rport <PORT>

msf auxiliary(scanner/ip/ipidseq) > set threads 2

msf auxiliary(scanner/ip/ipidseq) > run
```

---
## References

### Evasion

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x02 - Active Fingerprinting/Port Scanners/Network Mapper/Usage/04 - Evasion#^72346e|Network Mapper: Zombie Scan]]
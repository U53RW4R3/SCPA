# Masscan

## Help Menu

```
$ masscan --nmap
Masscan (https://github.com/robertdavidgraham/masscan)
Usage: masscan [Options] -p{Target-Ports} {Target-IP-Ranges}
TARGET SPECIFICATION:
  Can pass only IPv4/IPv6 address, CIDR networks, or ranges (non-nmap style)
  Ex: 10.0.0.0/8, 192.168.0.1, 10.0.0.1-10.0.0.254
  -iL <inputfilename>: Input from list of hosts/networks
  --exclude <host1[,host2][,host3],...>: Exclude hosts/networks
  --excludefile <exclude_file>: Exclude list from file
  --randomize-hosts: Randomize order of hosts (default)
HOST DISCOVERY:
  -Pn: Treat all hosts as online (default)
  -n: Never do DNS resolution (default)
SCAN TECHNIQUES:
  -sS: TCP SYN (always on, default)
SERVICE/VERSION DETECTION:
  --banners: get the banners of the listening service if available. The
    default timeout for waiting to receive data is 30 seconds.
PORT SPECIFICATION AND SCAN ORDER:
  -p <port ranges>: Only scan specified ports
    Ex: -p22; -p1-65535; -p 111,137,80,139,8080
TIMING AND PERFORMANCE:
  --max-rate <number>: Send packets no faster than <number> per second
  --connection-timeout <number>: time in seconds a TCP connection will
    timeout while waiting for banner data from a port.
FIREWALL/IDS EVASION AND SPOOFING:
  -S/--source-ip <IP_Address>: Spoof source address
  -e <iface>: Use specified interface
  -g/--source-port <portnum>: Use given port number
  --ttl <val>: Set IP time-to-live field
  --spoof-mac <mac address/prefix/vendor name>: Spoof your MAC address
OUTPUT:
  --output-format <format>: Sets output to binary/list/unicornscan/json/ndjson/grepable/xml
  --output-file <file>: Write scan results to file. If --output-format is
     not given default is xml
  -oL/-oJ/-oD/-oG/-oB/-oX/-oU <file>: Output scan in List/JSON/nDjson/Grepable/Binary/XML/Unicornscan format,
     respectively, to the given filename. Shortcut for
     --output-format <format> --output-file <file>
  -v: Increase verbosity level (use -vv or more for greater effect)
  -d: Increase debugging level (use -dd or more for greater effect)
  --open: Only show open (or possibly open) ports
  --packet-trace: Show all packets sent and received
  --iflist: Print host interfaces and routes (for debugging)
  --append-output: Append to rather than clobber specified output files
  --resume <filename>: Resume an aborted scan
MISC:
  --send-eth: Send using raw ethernet frames (default)
  -V: Print version number
  -h: Print this help summary page.
EXAMPLES:
  masscan -v -sS 192.168.0.0/16 10.0.0.0/8 -p 80
  masscan 23.0.0.0/0 -p80 --banners -output-format binary --output-filename internet.scan
  masscan --open --banners --readscan internet.scan -oG internet_scan.grepable
SEE (https://github.com/robertdavidgraham/masscan) FOR MORE HELP
```

## Usage

TODO: Provide more usage coverage for masscan

```
# masscan -p 80,443 --rate 1000 <IP>/<CIDR>
```

### Banner Grabbing

```
# masscan -p 80,443 --rate 1000 --banners <IP>/<CIDR>
```

### Exclude IP addresses

```
$ cat > block-ip-ranges.txt << EOF
0.0.0.0/8
10.0.0.0/8
127.0.0.0/8
169.254.0.0/16
172.16.0.0/12
192.168.0.0/16
203.0.113.0/24
240.0.0.0/4
255.255.255.255/32
EOF

# masscan -p 80,443 --open-only -Pn -sS --rate 10000 -S 8.8.8.8 --excludefile block-ip-ranges.txt --ranges 0.0.0.0/0 | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" > ips_output.txt
```

## Use Cases

### Scan Active Web Servers

```
# masscan 0.0.0.0/0 -p 80,443 --rate=1000 -oX webservers_output.xml
```

Extract IP address

```
$ xmllint --xpath '//host/address/@addr' webservers_output.xml | sed 's/ addr=/\n/g' | sed 's/"//g' | sed 's/^\s*//' > ips.txt

$ grep 'address addr' webservers_output.xml | cut -d '"' -f 2 > ips.txt
```

Retrieve online web servers.

```
$ httpx -silent -l ips.txt -p http:80,https:443 -mc 200 -o active_urls.txt
```

---
## References

### Github

- [Masscan](https://github.com/robertdavidgraham/masscan)

- [Blacklist IP ranges](https://gist.github.com/ozuma/fb21ab0f7143579b1f2794f4af746fb2)

### Enlace Hacktivista

- [Enlace Hacktivista: Initial Access Tactics, techniques and procedures](https://enlacehacktivista.org/index.php?title=Initial_Access_Tactics,_techniques_and_procedures)

- [InfoSecWarrior: Offensive Pentesting Host - Masscan](https://github.com/InfoSecWarrior/Offensive-Pentesting-Host/blob/main/Network%20Scanning/MASSCAN.md)

### Sickcodes

- [Sickcodes: ARIN Reserved IPv4 Address CIDR Blocks](https://gist.github.com/sickcodes/5e72643852e301aac84cf34a0348ef09)
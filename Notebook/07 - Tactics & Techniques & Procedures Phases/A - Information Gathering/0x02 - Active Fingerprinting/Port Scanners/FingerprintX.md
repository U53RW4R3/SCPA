---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - fingerprintx
---
# FingerprintX

## 01 - Setup

```
$ go install github.com/praetorian-inc/fingerprintx/cmd/fingerprintx@latest && \
sudo mv ~/go/bin/fingerprintx /usr/local/bin
```

## 02 - Help Menu

```
$ fingerprintx -h
Usage:
  fingerprintx [flags]
TARGET SPECIFICATION:
	Requires a host and port number or ip and port number. The port is assumed to be open.
	HOST:PORT or IP:PORT
EXAMPLES:
	fingerprintx -t praetorian.com:80
	fingerprintx -l input-file.txt
	fingerprintx --json -t praetorian.com:80,127.0.0.1:8000

Flags:
      --csv               output format in csv
  -f, --fast              fast mode
  -h, --help              help for fingerprintx
      --json              output format in json
  -l, --list string       input file containing targets
  -o, --output string     output file
  -t, --targets strings   target or comma separated target list
  -w, --timeout int       timeout (milliseconds) (default 2000)
  -U, --udp               run UDP plugins
  -v, --verbose           verbose mode
```

## 03 - Usage

Specify a single IP address and port.

```
$ fingerprintx -t <IP>:<PORT> -o output.txt
```

A list of IP addresses and ports.

```
$ fingerprintx -l ip_targets.txt -o output.txt
```

## 04 - Use Cases

### 4.1 - Port Scan

```
$ naabu -silent ip_targets.txt | fingerprintx -o output.txt
```

Enumerate the domains then perform a port scan.

```
$ subfinder -silent -dL domains.txt | naabu -silent ip_targets.txt | fingerprintx -o output.txt
```

---
## References

- [FingerprintX](https://github.com/praetorian-inc/fingerprintx)
# 10 - Internal Reconnaissance

Search Tag(s): #sliver #command-and-control #interactive-shell

```
whoami

getprivs

getuid

getpid

getgid
```

## Process Enumeration

```
sliver (IMPLANT_NAME) > ps -h
```

## Networking

### IP Address

```
sliver (IMPLANT_NAME) > ifconfig [-A]
```

### Netstat

- Help Menu

```
sliver > netstat -h

Print network connection information

Usage:
======
  netstat [flags]

Flags:
======
  -h, --help           display help
  -4, --ip4            display information about IPv4 sockets
  -6, --ip6            display information about IPv6 sockets
  -l, --listen         display information about listening sockets
  -n, --numeric        display numeric addresses (disable hostname resolution)
  -T, --tcp            display information about TCP sockets
  -t, --timeout int    command timeout in seconds (default: 60)
  -u, --udp            display information about UDP sockets
```
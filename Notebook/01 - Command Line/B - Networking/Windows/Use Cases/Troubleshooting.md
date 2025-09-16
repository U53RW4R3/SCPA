# Troubleshooting

## Network Latency

```
C:\> pathping.exe <dns_nameserver>
```

## Flush DNS

```
C:\> ipconfig.exe /flushdns
```

## Refresh IP Address

```
C:\> ipconfig.exe /release

C:\> ipconfig.exe /renew
```

## Reset Windows Sockets

```
C:\> netsh.exe winsock reset [C:\path\to\winsock_log.txt]

C:\> netsh.exe winsock reset proxy
```

## Reset TCP/IP Stack

```
C:\> netsh.exe int ip reset
```
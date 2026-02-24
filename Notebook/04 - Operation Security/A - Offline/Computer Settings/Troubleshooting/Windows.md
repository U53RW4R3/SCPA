# Windows

## 01 - Local

### 1.1 - Diagnose Power Efficiency

```
C:\> powercfg.exe /energy
```

### 1.2 - Check Boot Configuration

```
C:\> bcedit.exe /enum
```

### 1.3 - System Cleanup

Download missing components.

```
C:\> Dism.exe /Online /Cleanup-Image /Restorehealth
```

Checks if there's something wrong with the disk(s).

```
C:\> chdsk.exe <drive_letter>: /f /r /x
```

Repair files and remove unwanted programs (i.e. malware).

> [!WARNING] Before You Proceed!
> Create a system restore as a backup first.

```
C:\> sfc.exe /scannow
```

## 02 - Network

### 2.1 - Network Latency

```
C:\> pathping.exe <dns_nameserver>
```

### 2.2 - Flush DNS

```
C:\> ipconfig.exe /flushdns
```

### 2.3 - Refresh IP Address

```
C:\> ipconfig.exe /release

C:\> ipconfig.exe /renew
```

### 2.4 - Reset Windows Sockets

```
C:\> netsh.exe winsock reset [C:\path\to\winsock_log.txt]

C:\> netsh.exe winsock reset proxy
```

### 2.5 - Reset TCP/IP Stack

```
C:\> netsh.exe int ip reset
```
---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - dismap
---
# Dismap

## 01 - Setup

### 1.1 - Download Pre-compiled Binary

#### 1.1.1 - Linux

```
$ sudo wget -qO /usr/local/bin/dismap https://github.com/zhzyker/dismap/releases/download/v0.4/dismap-0.4-linux-amd64 && \
sudo chmod 755 /usr/local/bin/dismap

$ sudo curl -o /usr/local/bin/dismap https://github.com/zhzyker/dismap/releases/download/v0.4/dismap-0.4-linux-amd64 && \
sudo chmod 755 /usr/local/bin/dismap
```

#### 1.1.2 - Windows

Download the binary in command prompt.

```
C:\> certutil.exe -urlcache -split -f https://github.com/zhzyker/dismap/releases/download/v0.4/dismap-0.4-windows-amd64.exe dismap.exe

C:\> curl.exe -o dismap.exe https://github.com/zhzyker/dismap/releases/download/v0.4/dismap-0.4-windows-amd64.exe
```

Download the binary in PowerShell cmdlet.

```
PS C:\> Invoke-WebRequest -Uri https://github.com/zhzyker/dismap/releases/download/v0.4/dismap-0.4-windows-amd64.exe -OutFile dismap.exe
```

### 1.2 - Cross Compile

```
$ go install github.com/zhzyker/dismap@latest && \
cd dismap/cmd/dismap && go build -ldflags="-s -w " -trimpath && \
sudo cp dismap /usr/local/bin/
```

For embedded devices.

```
$ GOARCH=mipsle go build -ldflags="-s -w " -trimpath
```

#### 1.2.2 - Windows

```
$ GOOS=windows GOARCH=amd64 go build -ldflags="-s -w " -trimpath
```

## 02 - Help Menu

```
> dismap -h
_____________
______  /__(_)_____________ _________ ________
_  __  /__  /__  ___/_  __ `__ \  __ `/__  __ \
/ /_/ / _  / _(__  )_  / / / / / /_/ /__  /_/ /
\__,_/  /_/  /____/ /_/ /_/ /_/\__,_/ _  .___/
                                        /_/
  dismap version: 0.4 release
  author: zhzyker && Nemophllist
  from: https://github.com/zhzyker/dismap

  -f, --file string     Parse the target from the specified file for batch recognition
  -h, --help            Show help
  -i, --ip string       Network segment [e.g. -i 192.168.1.0/24 or -i 192.168.1.1-10]
  -j, --json string     Scan result in json format [e.g. -j r.json]
  -l, --level int       Specify log level (0:Fatal 1:Error 2:Info 3:Warning 4:Debug 5:Verbose) (default 3)
  -m, --mode string     Specify the protocol [e.g. -m mysql/-m http]
      --nc              Do not print character colors
      --np              Not use ICMP/PING to detect surviving hosts
  -o, --output string   Save the scan results to the specified file (default "output.txt")
  -p, --port string     Custom scan ports [e.g. -p 80,443 or -p 1-65535]
      --proxy string    Use proxy scan, support http/socks5 protocol [e.g. --proxy socks5://127.0.0.1:1080]
  -t, --thread int      Number of concurrent threads (default 500)
      --timeout int     Response timeout time, the default is 5 seconds (default 5)
      --type string     Specify the type [e.g. --type tcp/--type udp]
  -u, --uri string      Specify a target URI [e.g. -u https://example.com]
```

## 03 - Usage

TODO: Fill this info

```
> dismap -i <IP> -p 21-23

> dismap -i <IP> -p 135,445
```

```
> dismap -i <IP>/<CIDR>
```

```
> dismap -i <start_IP>-<end_IP>

> dismap -i 192.168.1.5-10
```

```
> dismap -u <scheme>://<IP>[:<PORT>]/ -m <protocol>
```

```
> dismap -f ips.txt
```

```
> dismap --type tcp --proxy socks5://<pivot_IP>:<pivot_PORT> -i <IP>

> dismap --type tcp --proxy http://<pivot_IP>:<pivot_PORT> -i <IP>
```

---
## References

### Source Repositories

- [Dismap](https://github.com/zhzyker/dismap)
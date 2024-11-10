# Retrieve Proxy Servers

## 01 - Download Public Proxies

SOCKS4

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks4&country=<country_code>

$ curl https://api.openproxylist.xyz/socks4.txt
```

SOCKS4A

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks4a&country=<country_code>
```

SOCKS5

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks5&country=<country_code>

$ curl https://api.openproxylist.xyz/socks5.txt
```

HTTP

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks5&country=<country_code>

$ curl https://api.openproxylist.xyz/http.txt
```

## 02 - ProxyFor

### 2.1 - Setup

#### 2.1.1 - Download Pre-compiled Binary

```
$ wget https://github.com/0xsha/ProxyFor/releases/download/v1.0.2/ProxyFor_1.0.2_Linux_x86_64.tar.gz && \
tar xzf ProxyFor_1.0.2_Linux_x86_64.tar.gz && rm ProxyFor_1.0.2_Linux_x86_64.tar.gz && \
sudo cp ProxyFor /usr/local/bin/
```

#### 2.1.2 - Compile

```
$ go install github.com/0xsha/ProxyFor@latest && \
sudo mv ~/go/bin/ProxyFor /usr/local/bin/
```

### 2.2 - Help Menu

```
$ ProxyFor -h
usage: ProxyChecker [-h|--help] [-t|--threads <integer>] [-r|--response
                    <integer>] -p|--path "<value>" [-d|--domain "<value>"]
                    [-o|--output "<value>"] [-T|--timeout <integer>]

                    Checks for valid proxies and write valid ones in file

Arguments:

  -h  --help      Print help information
  -t  --threads   Number of threads. Default: 40
  -r  --response  expected HTTP response code. Default: 200
  -p  --path      path to proxy.txt)
  -d  --domain    Domain to check proxies against it. Default:
                  https://httpbin.org/ip
  -o  --output    Output file. Default: out.txt
  -T  --timeout   timeout in seconds. Default: 10
```

### 2.3 - Usage

```
$ ProxyFor -p proxylist.txt -d https://google.com -o live_proxies.txt
```

## 03 - ScanSSH

```
$ sudo apt install -y scanssh
```

Create a temporary array then execute `scanssh` to begin scanning.

```
$ readarray -t proxies < proxies.txt

$ sudo scanssh -p -s <socks4 | socks5 | http-proxy> ${proxies[@]} | tee proxies.txt
```

## 04 - Network Mapper

```
$ nmap -p 1080 -Pn -n --script socks-open-proxy [--script-args "proxy.url=google.com,proxy.pattern=<pattern>"] <IP>

$ nmap -p 1080 -Pn -n -sS --max-retries 1 --min-parallelism 700 --open -T4 --script socks-open-proxy -iL targets.txt 2>/dev/null | grep -B 4 -A 2 "socks-open-proxy:" | tee -a socks_proxies_output.txt
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x00 - Exploitation/0xC - Password Cracking/Online/Network Protocols/Remote Services/SOCKS|Password Cracking: SOCKS]]

- [Network Mapper NSEDocs: socks-open-proxy Script](https://nmap.org/nsedoc/scripts/socks-open-proxy.html)

### Hunt for Open Proxies

- [IP Address Location](https://www.ipaddresslocation.org/cidr/ip-ranges.php)

- [Fun Over IP: Socks proxy servers scanning with nmap](https://funoverip.net/2010/11/socks-proxy-servers-scanning-with-nmap/)

### Publicly available proxy servers

- [Proxyscrape](https://api.proxyscrape.com)

- [OpenProxyList](https://api.openproxylist.xyz/)

#### Spys.me

- [spys.me: SOCKS Proxy Servers](https://spys.me/socks.txt)

- [spys.me: HTTP](https://spys.me/proxy.txt)

#### Github

- [TheSpeedX: PROXY-List](https://github.com/TheSpeedX/PROXY-List)

- [clarketm: proxy-list](https://github.com/clarketm/proxy-list)

- [jetkai: proxy-list](https://github.com/jetkai/proxy-list)

- [MuRongPIG: Proxy-Master](https://github.com/MuRongPIG/Proxy-Master)

- [Proxyifly: free-proxy-list](https://github.com/proxifly/free-proxy-list)
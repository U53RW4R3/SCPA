# Retrieve Proxy Servers

## 01 - Download Public Proxies

- SOCKS4

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks4&country=<country_code>

$ curl https://api.openproxylist.xyz/socks4.txt
```

- SOCKS4A

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks4a&country=<country_code>
```

- SOCKS5

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks5&country=<country_code>

$ curl https://api.openproxylist.xyz/socks5.txt
```

- HTTP

```
$ curl https://api.proxyscrape.com/?request=displayproxies&proxytype=socks5&country=<country_code>

$ curl https://api.openproxylist.xyz/http.txt
```

## 02 - ScanSSH

`$ sudo apt install -y scanssh`

```
$ readarray -t proxies < proxies.txt

$ sudo scanssh -p -s <socks4 | socks5 | http-proxy> ${proxies[@]} | tee proxies.txt
```

## 03 - Formatter

### 3.1 - Proxychains

Refer to [[Command Line/Operating Systems/Linux/Use Cases/Networking/Basic|ping sweep one liners]] to grab active proxy servers then pass it to the script that will format for proxychains

```bash
#!/bin/bash

PROXY="${1}"
FILE="${2}"
USERNAME="${3}"
PASSWORD="${4}"

IPV4_REGEX="\b([0-9]{1,3}\.){3}[0-9]{1,3}\b"

function scan() {
	local ip=()
    local port=()
    local temp=""

	# TODO: Some programs like proxychains accepts numeric IP addresses except privoxy
	# $(ping -c 1 "${temp}" | grep "bytes from" | grep -Eo "${IPV4_REGEX}" | sort -u)

	# TODO: add a flag for -s, --scan <icmp | tcp> when using with /dev/tcp/<IP>/<PORT>
    while read -r line
    do
	    # temp=$(echo "${line}" | grep -Eo "${IPV4_REGEX}")
        temp=$(echo "${line}" | cut -d ":" -f 1)

        if [[ $(ping -c 1 "${temp}" | grep "bytes from") ]]
        then
            ip+=("${temp}")
            port+=($(echo "${line}" | cut -d ":" -f 2))
        fi
    done < "${FILE}"
}

function format() {
    local ip=()
    local port=()
    local temp=""

	# TODO: add a flag for -s, --scan <icmp | tcp> when using with /dev/tcp/<IP>/<PORT>
    while read -r line
    do
	    # temp=$(echo "${line}" | grep -Eo "${IPV4_REGEX}")
        temp=$(echo "${line}" | cut -d ":" -f 1)

        if [[ $(ping -c 1 "${temp}" | grep "bytes from" | grep -Eo "${IPV4_REGEX}" | sort -u) ]]
        then
            ip+=("${temp}")
            port+=($(echo "${line}" | cut -d ":" -f 2))
        fi
    done < "${FILE}"
    
    for ((i=0; i<${#ip[@]}; i++))
    do
        if [[ ${PROXY,,} = "socks4" ]]
        then
            echo "${PROXY,,} ${ip[$i]} ${port[$i]}"
        elif [[ ${PROXY,,} = "socks5" ]]
        then
            echo "${PROXY,,} ${ip[$i]} ${port[$i]} ${USERNAME} ${PASSWORD}"
        elif [[ ${PROXY,,} = "http" ]]
        then
            echo "${PROXY,,} ${ip[$i]} ${port[$i]} ${USERNAME} ${PASSWORD}"
        fi
    done
}

function usage() {
    echo "Usage: $0 <SOCKS4 | SOCKS5 | HTTP> ips.txt <username> <password>"
}

# TODO: Make flag switches

if [ $# -lt 2 ] || [ $PROXY = "-h" ]
then
       usage
       exit 1
fi

format
```

### 3.2 - Privoxy

```bash
#!/bin/bash

# Name it as privoxy-formatter.sh

PROXY="${1}"
FILE="${2}"
USERNAME="${3}"
PASSWORD="${4}"

function usage() {
    echo "Usage: $0 <SOCKS4 | SOCKS5 | HTTP> ips.txt <username> <password>"
}

function format() {
    local ip=()
    local port=()
    local temp=""

    while read -r line
    do
        temp=$(echo "${line}" | cut -d ":" -f 1)
        
        if [[ $(ping -c 1 "${temp}" | grep "bytes from" | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b") ]]
        then
            ip+=("${temp}")
            port+=($(echo "${line}" | cut -d ":" -f 2))
        fi
    done < "${FILE}"
    
    for ((i=0; i<${#ip[@]}; i++))
    do
        if [[ ${PROXY,,} = "socks4" ]]
        then
            echo "forward-socks4a   /       ${ip[$i]}:${port[$i]}   ."
        elif [[ ${PROXY,,} = "socks5" ]]
        then
            echo "forward-socks5    /       ${USERNAME}:${PASSWORD}@${ip[$i]}:${port[$i]}   ."
        fi
    done
}

# TODO: Make flag switches

if [ $# -lt 2 ] || [ $PROXY = "-h" ]
then
       usage
       exit 1
fi

format
```

## 04 - Nmap

```
$ nmap -p 1080 -Pn -n --script socks-open-proxy [--script-args "proxy.url=google.com,proxy.pattern=<pattern>"] <IP>

$ nmap -p 1080 -Pn -n -sS --max-retries 1 --min-parallelism 700 --open -T4 --script socks-open-proxy -iL targets.txt 2>/dev/null | grep -B 4 -A 2 "socks-open-proxy:" | tee -a socks_proxies_output.txt
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/C - Initial Access/04 - Password Cracking/Online/Network Protocols/SOCKS/Nmap|Nmap: SOCKS]]

- [Nmap NSEDocs: Script socks-open-proxy](https://nmap.org/nsedoc/scripts/socks-open-proxy.html)

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
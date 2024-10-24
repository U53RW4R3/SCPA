# Scripts

## 01 - Socat

```bash
#!/bin/bash
function check_socat() {
	local paths=("/usr/bin/socat" "/bin/socat" "/usr/local/bin/socat")

	for path in "${paths[@]}"
	do
	    if [[ -e "${path}" ]]
	    then
            echo "${path}"
	        break
	    fi
	done
}

function usage() {
    read -d '' help << EOF
Usage:
    $(basename ${0}) [-v <verbosity>] -l <local_PORT> [-m <proxy_method>] [-s <proxy_IP>] [-p <proxy_PORT>] -r <remote_IP> -b <remote_PORT> [-f]
Flags:
    -v, --verbose                   Increase verbosity in socat. Avaliable values: 1,2,3,4.
								    Use up to 4 times; 2 are recommended.
    -l, --listener                  Create a listening local port
    -m, --method                    Specify a proxy method. "socks4a" is set by default if
								    not specified. Other avaliable options are: "socks4", and
								    "connect"
    -s, --server                    IP address of the SOCKS4A proxy server (127.0.0.1 is set by
                                    default if not specified)
    -p, --port                      Port of the SOCKS4A proxy server (9050 is set by default if
                                    not specified)
    -r, --remote                    The remote IP address to bind
    -b, --bindport                  The remote port to bind
    -f, --fork                      Fork the process in the background
    -h, --help                      Display help menu
EOF

    echo "${help}"
    exit 1
}

function main() {
	local proxy_address_head
    local SOCAT

    if [[ ${#} -eq 0 ]]
    then
        usage
    fi

    while [[ ${#} -gt 0 ]]
    do
        case ${1} in
            -v | --verbose)
                VERBOSE=${2}
                shift 2
                ;;
            -l | --listener)
                LISTENER=${2}
                shift 2
                ;;
            -m | --method)
                PROXY_METHOD="${2,,}"
                shift 2
                ;;
            -s | --server)
                PROXY_SERVER_IP="${2}"
                shift 2
                ;;
            -p | --port)
                PROXY_SERVER_PORT=${2}
                shift 2
                ;;
            -r | --remote)
                REMOTE_IP="${2}"
                shift 2
                ;;
            -b | --bindport)
                REMOTE_PORT=${2}
                shift 2
                ;;
            -f | --fork)
	            BACKGROUND=1
                shift
                ;;
            -h | --help)
                usage
                ;;
            *)
                echo "Invalid option: ${1}" >&2
                exit 1
                ;;
        esac
    done

    if [[ -n $(check_socat) ]]
    then
        SOCAT=$(check_socat)
    else
        echo "socat isn't installed!"
        exit 1
    fi

    if [[ -z "${LISTENER}" ]]
    then
        echo "Missing local port listener!"
        exit 1
    fi

    if [[ -z "${PROXY_METHOD}" ]]
    then
        PROXY_METHOD="socks4a"
    elif [[ "${PROXY_METHOD}" != "socks4" && "${PROXY_METHOD}" != "socks4a" && "${PROXY_METHOD}" != "connect" ]]
    then
	    echo "Unknown Proxy server method! Avaliable options: socks4, socks4a, and connect"
	    exit 1
    fi

    # Set to localhost by default.
    if [[ -z "${PROXY_SERVER_IP}" ]]
    then
        PROXY_SERVER_IP="127.0.0.1"
    fi

    # Set to TOR port by default.
    if [[ -z ${PROXY_SERVER_PORT} ]]
    then
        PROXY_SERVER_PORT=9050
    fi

    if [[ (-z "${REMOTE_IP}" || -z ${REMOTE_PORT}) ]]
    then
        echo "Specify the target's IP address and port to pivot."
        exit 1
    fi

    if [[ "${PROXY_METHOD}" == "socks4a" ]]
    then
	    proxy_address_head="socks4a:${PROXY_SERVER_IP}:${REMOTE_IP}:${REMOTE_PORT},socksport=${PROXY_SERVER_PORT}"
    elif [[ "${PROXY_METHOD}" == "socks4" ]]
    then
	    proxy_address_head="socks4:${PROXY_SERVER_IP}:${REMOTE_IP}:${REMOTE_PORT},socksport=${PROXY_SERVER_PORT}"
    elif [[ "${PROXY_METHOD}" == "connect" ]]
    then
	    proxy_address_head="proxy:${PROXY_SERVER_IP}:${REMOTE_IP}:${REMOTE_PORT},proxyport=${PROXY_SERVER_PORT}"
    fi

	if [[ ${VERBOSE} -eq 1 ]]
	then
		SOCAT+=" -d"
	elif [[ ${VERBOSE} -eq 2 ]]
	then
		SOCAT+=" -dd"
	elif [[ ${VERBOSE} -eq 3 ]]
	then
		SOCAT+=" -ddd"
	elif [[ ${VERBOSE} -eq 4 ]]
	then
		SOCAT+=" -dddd"
	fi

	if [[ ${BACKGROUND} -eq 1 ]]
	then
		nohup ${SOCAT} tcp4-listen:${LISTENER},reuseaddr,fork "${proxy_address_head}" </dev/null >/dev/null 2>&1 &
	else
		${SOCAT} tcp4-listen:${LISTENER},reuseaddr,fork "${proxy_address_head}"
	fi
}

main "${@}"
```

^9aa75c

Make it executable.

```
$ chmod 755 pivotbinder.sh
```

It'll set to localhost and TOR port (9050) to pivot to the target. To confirm it works increase the verbosity to 2.

```
$ ./pivotbinder.sh -v 2 -l <local_PORT> -r <remote_IP> -b <remote_PORT>
```

You can set a custom socks port.

```
$ ./pivotbinder.sh -l <local_PORT> -p <SOCKS_server_PORT> -r <remote_IP> -b <remote_PORT>
```

You can set socks proxy IP address and/or port to pivot. Including to choose 3 proxy server methods.

```
$ ./pivotbinder.sh -l <local_PORT> -m <socks4 | socks4a | connect> -s <SOCKS_server_IP> -p <SOCKS_server_PORT> -r <remote_IP> -b <remote_PORT>
```

You can fork it in the background. Once you're finished kill socat process.

```
$ ./pivotbinder.sh -v 2 -l <local_PORT> -r <remote_IP> -b <remote_PORT> -f

$ pkill socat
```

## 02 - Formatter

### 2.1 - Proxychains

Refer to [[Parse IP Addresses|ping sweep one liners]] to grab active proxy servers then pass it to the script that will format for proxychains

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

### 2.2 - Privoxy

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
# Scripts

## 01 - Socat

```bash
#!/bin/bash
function check_dependencies() {
    if [[ -z $(which socat) ]]
    then
        echo "socat isn't installed!"
        exit 0
    fi
}

function usage() {
    read -d '' help << EOF
Usage:
    $(basename ${0}) -l <local_PORT> [-s <proxy_IP>] [-p <proxy_PORT>] -r <remote_IP> -b <remote_PORT>
Flags:
    -l, --listener                  Create a listening local port
    -s, --server                    IP address of the SOCKS4A proxy server (127.0.0.1 is set by
                                    default if not specified)

    -p, --port                      Port of the SOCKS4A proxy server (9050 is set by default if
                                    not specified)

    -r, --remote                    The remote IP address to bind
    -b, --bindport                  The remote port to bind
    -h, --help                      Display help menu
EOF

    echo "${help}"
    exit 1
}

function main() {
    check_dependencies

    if [[ ${#} -eq 0 ]]
    then
        usage
    fi

    while [[ ${#} -gt 0 ]]
    do
        case ${1} in
            -l | --listener)
                LISTENER=${2}
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
            -h | --help)
                usage
                ;;
            *)
                echo "Invalid option: ${1}" >&2
                exit 1
                ;;
        esac
    done

    if [[ -z "${LISTENER}" ]]
    then
        echo "Missing local port listener!"
        exit 1
    fi

    # If input was empty. Set to localhost by default.
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

    socat TCP4-LISTEN:"${LISTENER}",fork SOCKS4A:"${PROXY_SERVER_IP}":"${REMOTE_IP}":"${REMOTE_PORT}",socksport="${PROXY_SERVER_PORT}" & > /dev/null
}

main "${@}"
```

^9aa75c

Make it executable.

```
$ chmod 755 proxybind.sh
```

It'll set to localhost and TOR port (9050) to pivot to the target.

```
$ ./proxybind.sh -l <local_PORT> -r <remote_IP> -b <remote_PORT>
```

You can set a custom SOCKS4A port.

```
$ ./proxybind.sh -l <local_PORT> -p <SOCKS_server_PORT> -r <remote_IP> -b <remote_PORT>
```

You can set socks proxy IP address and/or port to pivot.

```
$ ./proxybind.sh -l <local_PORT> -s <SOCKS_server_IP> -p <SOCKS_server_PORT> -r <remote_IP> -b <remote_PORT>
```

## 02 - Formatter

### 2.1 - Proxychains

Refer to [[01 - Command Line/A - Operating Systems/Linux/Use Cases/Networking/Basic|ping sweep one liners]] to grab active proxy servers then pass it to the script that will format for proxychains

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
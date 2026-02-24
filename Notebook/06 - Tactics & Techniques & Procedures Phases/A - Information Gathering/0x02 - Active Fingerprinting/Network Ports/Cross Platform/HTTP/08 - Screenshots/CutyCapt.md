---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - http
---
# #cutycapt

## 01 - Basic

Take a single screenshot

```
$ cutycapt --url=http[s]://<IP> --out=image.png
```

## 02 - Automation Script

```bash
#!/usr/bin/env bash

set -euo pipefail

function usage() {
    cat <<EOF
Usage: $0 -u <URL-or-file> -o <output_dir>

Options:
  -u <URL-or-file>   Either a single URL or a path to a file that contains
                     URLs (one per line). The script decides which based on
                     whether the argument is an existing regular file.
  -o <directory>    Output directory (required)
  -h                Show this help message
EOF
    exit 1
}

function save_screenshots() {
    local -n urls="${1}"
    local output_directory="${2}"

    local i=1
    for url in "${urls[@]}"
    do
        local path
        path=$(echo "${url}" | sed -e 's|^[a-z]\+://||' -e 's|/|__|g')
        [[ -z "${path}" ]] && path="home"

        local filename
        printf -v filename "%03d-%s.png" "${i}" "${path}"

        cutycapt --url="${url}" --out="${output_directory}/${filename}" \
                 --min-width=1280 --min-height=800 \
                 > /dev/null 2>&1

        ((i++))
    done
}

function main() {
    local url=""
    local output_directory=""

    while ((${#} > 0 ))
    do
        case "${1}" in
            -u)
                [[ -n "${2-}" ]] || usage
                url="${2}"
                shift 2
                ;;
            -o)
                [[ -n "${2-}" ]] || usage
                output_directory="${2}"
                shift 2
                ;;
            -h|--help)
                usage
                ;;
            *)
                echo "Unknown option: ${1}" >&2
                usage
                ;;
        esac
    done

    if [[ -z "${url}" || -z "${output_directory}" ]]
    then
        echo "Error: both -u and -o are required." >&2
        usage
    fi

    local -a url_list=()
    if [[ -f "${url}" ]]
    then
        # Read each non‑empty, non‑comment line
        while IFS= read -r line
        do
            [[ -z "${line}" || "${line}" =~ ^# ]] && continue
            url_list+=("${line}")
        done < "${url}"
    else
        url_list+=("${url}")
    fi

    if ((${#url_list[@]} == 0))
    then
        echo "Error: no URLs found to process." >&2
        exit 1
    fi

    if [[ -d "${output_directory}" ]]
    then
	    rm -rf "${output_directory}"
    fi

    mkdir -p "${output_directory}"

    save_screenshots url_list "$output_dir"
}


main "${@}"
```

## 03 - Use Cases

```
$ for ip in $(cat nmap-output.gnmap) | grep ":80$\|:443\|:8000\|:8080" | grep -v "Nmap" | awk '{print $2}'); do cutycapt --url=$ip --out=$ip.png;done

$ ls -1 *.png
10.11.1.10.png
10.11.1.115.png
10.11.1.116.png
10.11.1.128.png
10.11.1.13.png
10.11.1.133.png
10.11.1.14.png
10.11.1.202.png
10.11.1.209.png
10.11.1.217.png
```

Create a single report in a HTML file to view them.

```bash
#!/bin/bash
# Bash script to examine the scan results through HTML.

echo "<HTML><BODY><BR>" > web.html
ls -1 *.png | awk -F : '{ print $1":\n<BR><IMG SRC=\""$1""$2"\" width=600><BR>"}' >> web.html
echo "</BODY></HTML>" >> web.html
```

Run the script.

```
$ chmod +x ./pngtohtml.sh

$ ./pngtohtml.sh
```

Open it in a web browser.

```
$ firefox web.html
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/D - Webapp Pentesting/0x03 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents|Webapp Pentesting: User Agents]]
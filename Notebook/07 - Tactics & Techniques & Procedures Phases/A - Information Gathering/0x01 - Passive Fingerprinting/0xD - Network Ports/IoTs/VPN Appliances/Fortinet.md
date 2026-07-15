# Fortinet

## Dorks

```
http.html:"/remote/login" "xxxxxxxx"
http.favicon.hash:945408572
cpe:"cpe:2.3:o:fortinet:fortios"
```

## CLI Command

```
$ shodan download --limit 10000 fortinet_vpn_appliances.json.gz "http.html:'/remote/login' 'xxxxxxxx'"

$ shodan parse fortinet_vpn_appliances.json.gz --fields=ip_str,port > fortinet_vpn_ip_targets.txt
```

Sort by number of ports.

```
$ awk '{count[$2]++} END {for (port in count) print count[port], "occurrences - Port", port}' fortinet_ips.txt | sort -rn
```

To filter the specific port (for example 10443)

```
$ grep -E '\s10443$' fortinet_ips.txt | awk '{print $1}' > 10443_ips.txt
```
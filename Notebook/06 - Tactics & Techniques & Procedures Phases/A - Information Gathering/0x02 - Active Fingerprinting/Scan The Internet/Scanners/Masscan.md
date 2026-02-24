# #masscan

## Banner Grabbing

```
# masscan -p 80,443 --rate 1000 --banners <IP>/<CIDR>
```

## Exclude IP addresses

```
$ cat > block-ip-ranges.txt << EOF
0.0.0.0/8
10.0.0.0/8
127.0.0.0/8
169.254.0.0/16
172.16.0.0/12
192.168.0.0/16
203.0.113.0/24
240.0.0.0/4
255.255.255.255/32
EOF

# masscan -p 80,443 --open-only -Pn -sS --rate 10000 -S 8.8.8.8 --excludefile block-ip-ranges.txt --ranges 0.0.0.0/0 | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" > ips_output.txt
```

## Use Cases

### Scan Active Web Servers

```
# masscan 0.0.0.0/0 -p 80,443 --rate=100000 | awk '{ print $6 }' | sort -u > live_ips.txt

# masscan 0.0.0.0/0 -p 80,443 --rate=1000 -oX webservers_output.xml
```

Extract IP address

```
$ xmllint --xpath '//host/address/@addr' webservers_output.xml | sed 's/ addr=/\n/g' | sed 's/"//g' | sed 's/^\s*//' > ips.txt

$ grep 'address addr' webservers_output.xml | cut -d '"' -f 2 > ips.txt
```

Retrieve online web servers.

```
$ httpx -silent -l ips.txt -p http:80,https:443 -mc 200 -o active_urls.txt
```

---
## References

### Source Repositories

- [Masscan](https://github.com/robertdavidgraham/masscan)

- [Blacklist IP ranges](https://gist.github.com/ozuma/fb21ab0f7143579b1f2794f4af746fb2)

### Enlace Hacktivista

- [Enlace Hacktivista: Initial Access Tactics, techniques and procedures](https://enlacehacktivista.org/index.php?title=Initial_Access_Tactics,_techniques_and_procedures)

- [InfoSecWarrior: Offensive Pentesting Host - Masscan](https://github.com/InfoSecWarrior/Offensive-Pentesting-Host/blob/main/Network%20Scanning/MASSCAN.md)

### Sickcodes

- [Sickcodes: ARIN Reserved IPv4 Address CIDR Blocks](https://gist.github.com/sickcodes/5e72643852e301aac84cf34a0348ef09)
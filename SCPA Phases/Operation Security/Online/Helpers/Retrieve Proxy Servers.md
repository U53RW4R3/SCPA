# Retrieve Proxy Servers

## 01 - Nmap

```
$ nmap -p 1080 -Pn -n --script socks-open-proxy [--script-args "proxy.url=google.com,proxy.pattern=<pattern>"] <IP>

$ nmap -p 1080 -Pn -n -sS --max-retries 1 --min-parallelism 700 --open -T4 --script socks-open-proxy -iL targets.txt 2>/dev/null | grep -B 4 -A 2 "socks-open-proxy:" | tee -a socks_proxies_output.txt
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/Initial Access/Password Cracking/Online/Network Protocols/SOCKS/Nmap|Nmap: SOCKS]]

- [Nmap NSEDocs: Script socks-open-proxy](https://nmap.org/nsedoc/scripts/socks-open-proxy.html)

### Hunt for Open Proxies

- [IP Address Location](https://www.ipaddresslocation.org/cidr/ip-ranges.php)

- [Fun Over IP: Socks proxy servers scanning with nmap](https://funoverip.net/2010/11/socks-proxy-servers-scanning-with-nmap/)
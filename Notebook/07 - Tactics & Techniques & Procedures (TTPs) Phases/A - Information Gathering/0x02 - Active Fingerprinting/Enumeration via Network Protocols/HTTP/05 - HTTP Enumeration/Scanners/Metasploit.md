# Metasploit

TODO: Fill this info

```
msf > use auxiliary/scanner/http/scraper

msf auxiliary(scanner/http/scraper) > options

Module options (auxiliary/scanner/http/scraper):

   Name     Current Setting      Required  Description
   ----     ---------------      --------  -----------
   PATH     /                    yes       The test path to the page to analize
   PATTERN  <title>(.*)</title>  yes       The regex to use (default regex is a sample to grab page title)
   Proxies                       no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                        yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    80                   yes       The target port (TCP)
   SSL      false                no        Negotiate SSL/TLS for outgoing connections
   THREADS  1                    yes       The number of concurrent threads (max one per host)
   VHOST                         no        HTTP server virtual host


View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/scraper) > set path <uri_path>

msf auxiliary(scanner/http/scraper) > set pattern <regex>

msf auxiliary(scanner/http/scraper) > set threads 2

msf auxiliary(scanner/http/scraper) > set rhosts <target_IP_1>,<target_IP_2>,<target_IP_n>

msf auxiliary(scanner/http/scraper) > set rport <PORT>

msf auxiliary(scanner/http/scraper) > run
```

HTTP Title

```
msf > use auxiliary/scanner/http/title
```

HTTP Header

```
msf > use auxiliary/scanner/http/http_header
```

HTTP Strict Transport Security (HSTS) Detection

```
msf > use auxiliary/scanner/http/http_hsts
```

Docker HTTP version

```
msf > use auxiliary/scanner/http/docker_version
```


```
msf > use auxiliary/scanner/http/open_proxy
```

```
msf > use auxiliary/scanner/http/squid_pivot_scanning
```

---
## References

- [[ProxyTunnel]]

- [Hacktricks: Pentesting Squid](https://book.hacktricks.xyz/network-services-pentesting/3128-pentesting-squid)
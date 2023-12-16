# 09 - HTTP Enumeration

## 9.1 - Nmap

`$ nmap -p 80,443,8080 -Pn -n -sV --script http-enum <IP>`

- Find open redirects

`$ nmap -p 80,443 -Pn -n --script http-open-redirect <IP>`

- Crawl the website and return any error pages.

`$ nmap -p 80,443,8080 -Pn -n --script http-errors`

- Discover open HTTP proxy

`$ nmap -p 80,443,8080 -Pn -n --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>`

## 9.2 - Metasploit

TODO: Fill this information

`msf > use auxiliary/scanner/http/open_proxy`
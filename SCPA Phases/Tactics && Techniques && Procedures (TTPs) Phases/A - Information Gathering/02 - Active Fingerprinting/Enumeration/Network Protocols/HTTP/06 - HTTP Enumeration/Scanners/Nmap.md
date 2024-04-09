# Nmap

- Enumerate HTTP, service version and some common directories.

`$ nmap -p 80,443,8080 -Pn -n -sV --script http-enum --script-args http.useragent='<user_agent>' <IP>`

- Find backup folders.

`$ nmap -p 80,443 -Pn -n --script http-backup-finder --script-args http.useragent='<user_agent>' <IP>`

- Get PHP version.

`$ nmap -p 80,443 -Pn -n --script http-php-version --script-args http.useragent='<user_agent>' <IP>`

- Find open redirects.

`$ nmap -p 80,443 -Pn -n --script http-open-redirect --script-args http.useragent='<user_agent>' <IP>`

- Crawl the website and return any error pages.

`$ nmap -p 80,443,8080 -Pn -n --script http-errors --script-args http.useragent='<user_agent>' <IP>`

- Discover open HTTP proxy.

`$ nmap -p 80,443,3128,8080 -Pn -n --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>`

---
## References

- [[User Agents]]

- [[ProxyTunnel]]
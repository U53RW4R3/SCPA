# Nmap

- Enumerate HTTP and service version

`$ nmap -p 80,443,8080 -Pn -n -sV --script http-enum <IP>`

- Find backup folders

`$ nmap -p 80,443 -Pn -n --script http-backup-finder <IP>`

- Get PHP version

`$ nmap -p 80,443 -Pn -n --script http-php-version <IP>`

- Find open redirects

`$ nmap -p 80,443 -Pn -n --script http-open-redirect <IP>`

- Crawl the website and return any error pages.

`$ nmap -p 80,443,8080 -Pn -n --script http-errors`

- Discover open HTTP proxy

`$ nmap -p 80,443,8080 -Pn -n --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>`
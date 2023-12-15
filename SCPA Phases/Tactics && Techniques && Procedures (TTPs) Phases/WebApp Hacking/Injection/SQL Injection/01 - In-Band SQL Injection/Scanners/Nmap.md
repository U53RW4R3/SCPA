# Nmap

Search Tag(s): #nmap #sql-injection #http

- It'll scan for GET and POST request parameters

`$ nmap -p80,443 -Pn -n --script http-sql-injection [--script-args="http-sql-injection.url=<spider/start/path/to/URL>"] <IP>`

---
## References

- [Hacking Articles: Exploiting Sql Injection with Nmap and Sqlmap](https://www.hackingarticles.in/exploiting-sql-injection-nmap-sqlmap/)
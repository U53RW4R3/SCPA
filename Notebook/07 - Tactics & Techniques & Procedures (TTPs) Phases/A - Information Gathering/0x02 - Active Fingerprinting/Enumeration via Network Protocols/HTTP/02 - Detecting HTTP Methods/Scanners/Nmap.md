# Nmap

Test all HTTP methods

```
$ nmap -p 80,443,8000,8080,8443 -Pn -n -sV --script http-methods --script-args "http-methods.test=all,http-methods.url-path='/path/to/uri'[,http.useragent='<User_Agent>']" <IP>
```
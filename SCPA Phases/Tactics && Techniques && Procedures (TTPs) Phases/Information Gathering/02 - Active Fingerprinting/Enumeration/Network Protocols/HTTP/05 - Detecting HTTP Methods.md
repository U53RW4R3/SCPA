# 05 - Detecting HTTP Methods

## 5.1 - Manual

```
$ nc <IP> <PORT>
OPTIONS http[s]://<IP> HTTP/1.1
```

## 5.2 - Nmap

- Test all HTTP methods

`$ nmap -p 80,443 -sV --script http-methods --script-args http-methods.test=all <IP>`

- Discover open HTTP proxy

`$ nmap -p 80,443,8080 --script http-open-proxy --script-args proxy.url=<URL>,proxy.pattern=<pattern> <IP>`
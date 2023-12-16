# 05 - Detecting HTTP Methods

## 5.1 - Manual

```
$ nc <IP> <PORT>
OPTIONS http[s]://<IP> HTTP/1.1
```

## 5.2 - Nmap

- Test all HTTP methods

`$ nmap -p 80,443 -Pn -n -sV --script http-methods --script-args http-methods.test=all <IP>`

## 5.3 - Metasploit

TODO: Fill this information

`msf > use auxiliary/scanner/http/options`
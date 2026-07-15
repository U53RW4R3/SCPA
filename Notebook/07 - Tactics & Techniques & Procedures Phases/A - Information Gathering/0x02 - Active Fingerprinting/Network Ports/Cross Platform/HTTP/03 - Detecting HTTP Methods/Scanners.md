---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - http
---
# Scanners

## 01 - #nuclei

```
$ nuclei -u <URL> -t ~/nuclei-templates -id options-method
```

## 02 - #nikto

```
$ nikto -host <URL> -Plugins httpoptions
```

## 03 - #network-mapper

```
$ nmap -p 80,443,8000,8080,8443 -Pn -n -sV --script http-methods --script-args "http-methods.test=all,http-methods.url-path='/path/to/uri'[,http.useragent='<User_Agent>']" <IP>
```

## 04 - #metasploit

```
msf > use auxiliary/scanner/http/options

msf auxiliary(scanner/http/options) > run rhosts=<IP> rport=<PORT>
```
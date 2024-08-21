# Scanners

## 01 - Nuclei

```
$ nuclei -u <URL> -t ~/nuclei-templates -id options-method
```

## 02 - Nikto

```
$ nikto -h <URL> -Plugins httpoptions
```

## 03 - Nmap

```
$ nmap -p 80,443,8000,8080,8443 -Pn -n -sV --script http-methods --script-args "http-methods.test=all,http-methods.url-path='/path/to/uri'[,http.useragent='<User_Agent>']" <IP>
```

## 04 - Metasploit

TODO: Fill this info

```
msf > use auxiliary/scanner/http/options
```
# Authentication Methods

## 01 - [[Nuclei|Nuclei]]

```
$ nuclei -u <URL> -t ~/nuclei-templates -id basic-auth-detect
```

## 02 - Network Mapper

```
$ nmap -p 80,443,8000,8080,8443 -Pn -n --script http-auth --script-args http-auth.path=/login[,http.useragent='<user_agent>'] <IP>
```

Find authentication method from the URL.

```
$ nmap -p 80,443,8000,8080,8443 -Pn -n --script http-auth-finder [--script-args http-auth-finder.url=/path/to/url,http.useragent='<user_agent>'] <IP>
```

^4854b0

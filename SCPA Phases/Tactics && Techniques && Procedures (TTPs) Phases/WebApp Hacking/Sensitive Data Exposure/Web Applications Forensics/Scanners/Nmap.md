# Nmap

- Probe HTML and JavaScript comments to search for sensitive data.

`$ nmap -p80,443 --script http-comments-displayer --script-args http.useragent='<user_agent>' <IP>`

- Find configuration backup files.

`$ nmap -p80,443 --script http-config-backup --script-args http.useragent='<user_agent>' <IP>`

- Find exposed git config repositories.

`$ nmap -p 80,443,8080 -Pn -n -sV --script http-git --script-args http.useragent='<user_agent>' <IP>`

- Enumerate SVN config repositories.

```
$ nmap -p 80,443 -Pn -n -sV --script http-svn-info --script-args http.useragent='<user_agent>' <IP>

$ nmap -p 80,443 -Pn -n -sV --script http-svn-enum --script-args http.useragent='<user_agent>' <IP>
```

- Extract metadata

`$ nmap -p 80,443 -Pn -n --script http-exif-spider --script-args http.useragent='<user_agent>' <IP>`
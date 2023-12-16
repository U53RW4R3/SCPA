# Nmap

- Find HTML and JavaScript comments to find sensitive data.

`$ nmap -p80,443 --script http-comments-displayer <IP>`

- Find configuration backup files.

`$ nmap -p80,443 --script http-config-backup <IP>`

- Find exposed git config repositories.

`$ nmap -p 80,443,8080 -Pn -n -sV --script http-git <IP>`

- Enumerate SVN config repositories.

```
$ nmap -p 80,443 -Pn -n -sV --script http-svn-info <IP>

$ nmap -p 80,443 -Pn -n -sV --script http-svn-enum <IP>
```

- Extract metadata

`$ nmap -p 80,443 -Pn -n --script http-exif-spider <IP>`
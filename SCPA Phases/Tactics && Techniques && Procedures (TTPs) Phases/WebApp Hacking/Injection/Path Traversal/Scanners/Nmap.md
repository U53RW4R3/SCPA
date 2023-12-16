# Nmap

- Probe path traversal vulnerability.

`$ nmap -p 80,443 -Pn -n --script http-passwd --script-args http-passwd.root=/path/to/URI/`

- Probe remote file inclusion vulnerability.

```
$ nmap -p 80,443 -PN -n --script http-rfi-spider --script-args http-rfi-spider.inclusionurl=https://google.com <IP>
```
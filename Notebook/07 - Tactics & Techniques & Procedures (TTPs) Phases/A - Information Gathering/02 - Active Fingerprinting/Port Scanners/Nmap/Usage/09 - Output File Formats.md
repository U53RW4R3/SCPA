# 09 - Output File Formats

Normal output format

```
$ sudo nmap -oN initial.nmap <IP>
```

- 1337 5P34K 0U7PU7 F0rM47

```
$ sudo nmap -oS initial.nmap <IP>
```

XML output format

```
$ sudo nmap -oX initial.xml <IP>
```

Grepable output format

```
$ sudo nmap -oG initial.gnmap <IP>
```

All output formats

```
$ sudo nmap -oA initial <IP>
```

## 9.1 - Rover Nmap IP Addresses

```
$ grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' initial.nmap > ip_targets.txt

$ awk '/is up/ {print up}; {gsub (^(||)/,""); up = $NF}' initial.nmap > ip_targets.txt
```



```
$ a=$(grep -oP '\d{1,5}/open' initial.gnmap | sort -u |sed -e 's/\/open//g' | tr '\n' ','); a=${a::-1}
```
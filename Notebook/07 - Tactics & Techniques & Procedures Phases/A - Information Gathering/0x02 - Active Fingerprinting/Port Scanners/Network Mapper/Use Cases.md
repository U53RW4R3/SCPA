# Use Cases

## 01 - Longer UDP Scan

```
$ sudo nmap -sUVC -Pn --disable-arp-ping -oA initial <IP>
```

## 02 - Rover IP Addresses

```
$ grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' initial.nmap > ip_targets.txt

$ awk '/is up/ {print up}; {gsub (^(||)/,""); up = $NF}' initial.nmap > ip_targets.txt
```

```
$ a=$(grep -oP '\d{1,5}/open' initial.gnmap | sort -u | sed -e 's/\/open//g' | tr '\n' ','); a=${a::-1}
```
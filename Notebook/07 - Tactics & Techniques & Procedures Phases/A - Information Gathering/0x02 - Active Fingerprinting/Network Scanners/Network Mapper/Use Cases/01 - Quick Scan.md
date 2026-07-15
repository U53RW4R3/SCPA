# 01 - Quick Scan

TODO: Provide more use cases

## 1.1 - Quick Hosts Discovery

```
$ nmap -sn <IP>/<CIDR> | grep "Nmap" | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" > hosts.txt

$ nmap -sn -T4 -oG - <IP>/<CIDR> | grep "Status: Up" | cut -f 2 -d ' ' > hosts.txt
```

## 1.2 - Quick Scan with OS Detection

```
$ sudo nmap [-Pn] -n -sV --version-light -F -O --min-hostgroup 96 -T4 <IP>/<CIDR>
```

## 1.3 - Quick Scan of large networks in Nmap

```
$ sudo nmap -n -F --min-hostgroup 96 -T4 <IP>/<CIDR>

$ sudo nmap -sn -PE -n --min-hostgroup 1024 --min-parallelism 1024 -oX output.xml <IP>/<CIDR>
```

---
## References

### Network Mapper

- [Nmap Book: Scan a Largest Network for a Certain Open TCP Port](https://nmap.org/book/solution-find-open-port.html)

### Ethical hacking and penetration testing

- [Ethical hacking and penetration testing: Network Mapper usage tips](https://miloserdov.org/?p=3639)
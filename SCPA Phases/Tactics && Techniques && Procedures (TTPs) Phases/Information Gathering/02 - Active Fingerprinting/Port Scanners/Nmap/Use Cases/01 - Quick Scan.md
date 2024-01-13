# 01 - Quick Scan

TODO: Provide more use cases

## Quick Scan with OS Detection

```
$ sudo nmap [-Pn] -n -sV --version-light -F -O --min-hostgroup 96 -T4 <IP>/<CIDR>
```

## Quick Scan of large networks in Nmap

```
$ sudo nmap -n -F --min-hostgroup 96 -T4 <IP>/<CIDR>

$ sudo nmap -sn -PE -n --min-hostgroup 1024 --min-parallelism 1024 -oX output.xml <IP>/<CIDR>
```

---
## References

- [Nmap Book: Scan a Larget Network for a Certain Open TCP Port](https://nmap.org/book/solution-find-open-port.html)

- [Nmap usage tips](https://miloserdov.org/?p=3639)
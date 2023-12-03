# 01 - Quick Scan

TODO: Provide more use cases

## Quick Scan with OS Detection

```
$ sudo nmap --min-hostgroup 96 -Sv -T4 -n -O -F --version-light <IP>/<CIDR>
```

## Quick Scan of large networks in Nmap

```
$ sudo nmap --min-hostgroup 96 -T4 -n -F <IP>/<CIDR>

$ sudo nmap -sn -PE -n --min-hostgroup 1024 --min-parallelism 1024 -oX output.xml <IP>/<CIDR>
```

---
## References

- [Nmap usage tips](https://miloserdov.org/?p=3639)
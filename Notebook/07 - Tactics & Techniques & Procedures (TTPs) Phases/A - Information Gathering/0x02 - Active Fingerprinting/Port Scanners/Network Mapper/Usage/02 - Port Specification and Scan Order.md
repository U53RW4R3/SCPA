# 02 - Port Specification and Scan Order

Specify port(s) to scan.

```
$ nmap -p <PORT>

$ nmap -p 25,53,80,443
```

Port range and list to scan

```
$ nmap -p 21-23 <IP>

$ nmap -p 21-23,25,53,80 <IP>
```

Scan all ports

```
$ nmap -p- <IP>
```

Show open ports

```
$ nmap --open <IP>
```

---
## References

- [Network Mapper usage tips](https://miloserdov.org/?p=3639)
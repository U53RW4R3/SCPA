# Enable Sandbox

## Firejail

```
$ firejail --seccomp --nonewprivs --private --private-dev --private-tmp --net=none --x11 --whitelist=/tmp/file.pdf evince /tmp/file.pdf
```

---
## References

### Source Repositories

- [netblue30: firejail](https://github.com/netblue30/firejail)

### Null Byte

- [Null Byte: Locking Down Linux - Using Ubuntu as Your Primary OS, Part 3 (Application Hardening & Sandboxing)](https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-3-application-hardening-sandboxing-0185710/)
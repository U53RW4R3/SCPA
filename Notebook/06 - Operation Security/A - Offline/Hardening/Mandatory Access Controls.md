# Mandatory Access Controls

## AppArmor

```
# systemctl enable apparmor.service

# systemctl start apparmor.service

# aa-enforce /etc/apparmor.d/*
```

## SELinux

> [!INFO] System Restart Required
> Rebooting the system is required to apply changes.

```
# setenforce 1
```

```
# echo -e "SELINUX=enforcing\nSELINUXTYPE=targeted" > /etc/selinux/config
```

```
# echo -e "SELINUX=enforcing\nSELINUXTYPE=mls" > /etc/selinux/config
```

---
## References

### Null Byte

- [Null Byte: Locking Down Linux - Using Ubuntu as Your Primary OS, Part 3 (Application Hardening & Sandboxing)](https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-3-application-hardening-sandboxing-0185710/)
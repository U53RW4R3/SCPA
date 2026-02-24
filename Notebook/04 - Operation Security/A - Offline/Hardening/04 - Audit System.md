# 04 - Audit System

## 4.1 - Packages

Check packages' integrity using a package manager.

```
$ debsums

$ rpm -Va

$ rpm --verify <package_name>

$ rpm -qi <package_name>
```

## 4.2 - System

Perform whole system audit.

```
$ ./lynis audit system

$ firejail --audit
```

---
## References

### Null Byte

- [Null Byte: Locking Down Linux - Using Ubuntu as Your Primary OS, Part 4 (Auditing, Antivirus & Monitoring)](https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-4-auditing-antivirus-monitoring-0185572/)
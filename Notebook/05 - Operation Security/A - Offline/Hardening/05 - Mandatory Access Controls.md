# 05 - Mandatory Access Controls

## 5.1 - [[System Hardening|AppArmor]]

### 5.1.1 - Status

Check if it is enabled.

```
# aa-enabled
```

Check the status.

```
# aa-status
```

Display the loaded policies

```
# aa-status --profiled
```

### 5.1.2 - Profiles

Reload all profiles.

```
# systemctl reload apparmor.service
```

Enforce all profiles.

```
# aa-enforce /etc/apparmor.d/*
```

## 5.2 - [[System Hardening|SELinux]]

TODO: Fill this info

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
# 05 - Mandatory Access Controls

## 5.1 - AppArmor

### 5.1.1 - Setup

Install it according to your package manager.

```
$ sudo apt install -y apparmor apparmor-profiles apparmor-utils

$ sudo pacman -S --noconfirm apparmor
```

Enable the daemon service.

```
# systemctl enable apparmor.service

# systemctl start apparmor.service
```

### 5.1.2 - Status

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

### 5.1.3 - Profiles

Reload all profiles.

```
# systemctl reload apparmor.service
```

Enforce all profiles.

```
# aa-enforce /etc/apparmor.d/*
```

## 5.2 - SELinux

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
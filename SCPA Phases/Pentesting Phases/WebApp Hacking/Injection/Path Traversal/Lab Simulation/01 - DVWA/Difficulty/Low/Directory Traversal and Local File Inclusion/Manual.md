# Manual

## Directory Traversal

Navigating directories

### Linux

```
/etc/passwd
```

### Windows

```
/windows/win.ini
\\localhost\c$\windows\win.ini
```

## Local File Inclusion (LFI)

### General

#### Enumeration

- Check for disable_functions

```
phpinfo.php
```

### Linux

```
/etc/group
/etc/shadow
/home/<username>/.ssh/id_rsa
/root/.ssh/id_rsa
/etc/crontab
/home/<username>/.bash_history
/etc/ssh/sshd_config
```

### Windows

```
/WINDOWS/repair/sam
/WINDOWS/repair/system
```

---
## References

- [Hacking Articles: Comprehensive Guide on Path Traversal](https://www.hackingarticles.in/comprehensive-guide-on-path-traversal/)

- [SecurityIdiots: Guide to LFI](https://securityidiots.com/Web-Pentest/LFI/guide-to-lfi.html)

- [BorderGate: Local File Inclusion (LFI) Attacks](https://www.bordergate.co.uk/local-file-inclusion-attacks/)
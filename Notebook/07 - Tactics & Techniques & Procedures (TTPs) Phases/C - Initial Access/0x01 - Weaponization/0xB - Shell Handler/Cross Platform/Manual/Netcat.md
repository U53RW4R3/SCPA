---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - netcat
---
# Netcat

## 01 - Reverse Shell Handler

```
$ nc -lnvp <PORT>
```

Any listening ports ranging between **1-1023** must be ran as `root`.

```
$ sudo nc -lnvp 80
```

## 02 - Bind Shell Handler

```
$ nc -lnvp <target_IP> <target_PORT>
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Windows/Payloads/One-Liners/Netcat]]
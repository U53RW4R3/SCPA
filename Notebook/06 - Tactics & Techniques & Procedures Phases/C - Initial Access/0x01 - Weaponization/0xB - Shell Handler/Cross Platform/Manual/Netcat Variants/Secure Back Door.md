---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - sbd
---
# Secure Back Door

## 01 - Reverse Shell Handler

```
$ sbd -lnvp <PORT>
```

Any listening ports ranging between **1-1023** must be ran as `root`.

```
$ sudo sbd -lnvp 80
```

## 02 - Bind Shell Handler

```
$ sbd -lnvp <target_IP> <target_PORT>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Payloads/Cross Platform/One-Liners/Netcat Variants/Secure Back Door]]

### Kali Tools

- [Kali.org Tools: Secure Back Door](https://www.kali.org/tools/sbd/)
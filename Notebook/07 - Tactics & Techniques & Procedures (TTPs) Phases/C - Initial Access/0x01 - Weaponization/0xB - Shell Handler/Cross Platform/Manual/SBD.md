---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - sbd
---
# SBD

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

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Cross Platform/Payloads/One-Liners/SBD]]

### Kali Tools

- [Kali.org Tools: SBD](https://www.kali.org/tools/sbd/)
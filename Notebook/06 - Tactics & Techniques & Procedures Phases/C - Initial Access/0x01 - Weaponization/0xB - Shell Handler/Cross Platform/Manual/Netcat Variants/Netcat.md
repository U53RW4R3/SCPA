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

> [!IMPORTANT] Elevated Privileges are Required
> Any listening ports ranging between **1-1023** must be ran as `root`.

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

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/Netcat/Manual]]

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Payloads/Desktop/Windows/One-Liners/Netcat]]
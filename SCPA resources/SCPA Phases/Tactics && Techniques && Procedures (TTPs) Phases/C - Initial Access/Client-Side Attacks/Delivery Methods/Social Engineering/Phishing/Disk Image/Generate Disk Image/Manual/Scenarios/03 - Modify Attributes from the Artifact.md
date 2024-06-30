# 03 - Modify Attributes from the Artifact

Search Tag(s): #initial-foothold #defense-evasion #windows #use-cases

Make the file hidden.

```
$ setfattr -n user.DOSATTRIB -v 0x02 /mnt/ntfs/file.txt

$ getfattr -n user.DOSATTRIB /mnt/ntfs/file.txt
```

Make the file visible.

```
$ setfattr -n user.DOSATTRIB -v 0x00 /mnt/ntfs/file.txt

$ getfattr -n user.DOSATTRIB /mnt/ntfs/file.txt
```

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Defense Evasion/10 - Hide Artifacts/Alternate Data Streams (ADS)/Living off the Land|Windows: Hide Artifacts]]
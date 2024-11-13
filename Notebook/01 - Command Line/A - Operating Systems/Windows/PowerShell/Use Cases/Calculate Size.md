---
author(s):
  - Userware
tags:
  - command-line
  - use-cases
  - windows
---
# Calculate the size of the data

## 01 - Bytes

```
PS C:\> Get-ChildItem -Path [<drive_letter>:\]path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum

PS C:\> Get-ChildItem -Path \\<IP>\<share_name>\path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum

PS C:\> Get-ChildItem -Path [<drive_letter>:\]path\to\directory\ -Recurse -File | Measure-Object -Sum Length | Select-Object Count, Sum

PS C:\> Get-ChildItem -Path \\<IP>\<share_name>\path\to\directory\ -Recurse -File | Measure-Object -Sum Length | Select-Object Count, Sum
```

## 02 - Kilobytes

```
PS C:\> (Get-ChildItem -Path [<drive_letter>:\]path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum).Sum / 1Kb

PS C:\> (Get-ChildItem -Path \\<IP>\<share_name>\path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum).Sum / 1Kb
```

## 03 - Megabytes

```
PS C:\> (Get-ChildItem -Path [<drive_letter>:\]path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum).Sum / 1Mb

PS C:\> (Get-ChildItem -Path \\<IP>\<share_name>\path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum).Sum / 1Mb
```

## 04 - Gigabytes

```
PS C:\> (Get-ChildItem -Path [<drive_letter>:\]path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum).Sum / 1Gb

PS C:\> (Get-ChildItem -Path \\<IP>\<share_name>\path\to\directory\ -Recurse -File | Measure-Object -Property Length -Sum).Sum / 1Gb
```

---
## References

### Backlinks

- [[Windows PowerShell Cmdlet References]]
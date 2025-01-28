---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - windows
---
# ForFiles

Syntax as it follows.

```
C:\> forfiles.exe /p C:\path\to\search\ /m <match_file> /c "<commands>"
```

Searches the path in `C:\Windows\System32\` to look for a file `notepad.exe` to match to execute the implant.

```
C:\> forfiles.exe /p C:\Windows\System32\ /m notepad.exe /c implant.exe
```

---
## References

### LOLBAS

- [LOLBAS: Forfiles](https://lolbas-project.github.io/lolbas/Binaries/Forfiles/)
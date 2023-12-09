# 03 - Process Manipulation

Search Tag(s): #command-line #windows

## 2.1 - List Processes

### 2.1.1 - Display Processes

```
PS C:\> Get-Process

PS C:\> Get-Process -IncludeUserName

PS C:\> Get-CimInstance -ClassName Win32_Process | Select-Object CommandLine

PS C:\> Get-WMiObject -ClassName Win32_Process 
```

## 2.2 - Terminate Processes

### 2.2.1 -Terminate Process

`PS C:\> Stop-Process notepad.exe`

## 2.3 - Fork Background Process

`PS C:\> Start-Process [-FilePath] <command> -NoNewWindow -ArgumentList ("arg_1","arg_2","arg_n") [-WorkingDirectory C:\path\to\directory]`

---
## References

- [[Windows Powershell Cmdlet References]]

- [Malicious.link: Get Process List](https://room362.com/posts/2020/get-process-list/)
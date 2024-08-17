# 03 - Process Manipulation

Search Tag(s): #command-line #windows

## 3.1 - List Processes

### 3.1.1 - Display Processes

```
C:\> tasklist /v

C:\> tasklist /svc

C:\> tasklist /fi "imagename eq <process.exe>"

C:\> wmic process list full

C:\> wmic process list brief

C:\> wmic PATH Win32_Process GET Caption, Processid, Commandline

C:\> wmic PATH Win32_Process GET Caption,Name,OSName,ExecutablePath,ProcessId,WindowsVersion,CommandLine

C:\> wmic PATH Win32_Process GET Caption,Name,OSName,ExecutablePath,ProcessId,WindowsVersion,ParentProcessId,SessionId,CommandLine
```

## 3.2 - Terminate Processes

### 3.2.1 - Kill Process

```
C:\> taskkill /pid <PID> /f

C:\> taskkill /im <process.exe> /f

C:\> wmic process where "Name Like '<process.exe>'" call terminate
```

## 3.3 - Fork Background Process

```
C:\> start /b <command> [args]
```

---
## References

- [[Windows Command Prompt References]]

- [Malicious.link: Get Process List](https://room362.com/posts/2020/get-process-list/)
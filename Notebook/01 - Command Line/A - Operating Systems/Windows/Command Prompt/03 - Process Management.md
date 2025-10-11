---
author(s):
  - Userware
tags:
  - command-line
  - windows
---
# 03 - Process Management

## 3.1 - List Processes

### 3.1.1 - Display Processes

Display verbose information of the processes.

```
C:\> tasklist.exe /v

C:\> wmic.exe process list full
```

Display the services associated with the processes.

```
C:\> tasklist.exe /svc
```

Filter a specific process name.

```
C:\> tasklist.exe /fi "imagename eq <process.exe>"
```

```
C:\> wmic.exe Process LIST BRIEF

C:\> wmic.exe Process WHERE "name='<process_name>'" GET ProcessId

C:\> wmic.exe PATH Win32_Process GET Caption, Processid, Commandline

C:\> wmic.exe PATH Win32_Process GET Caption,Name,OSName,ExecutablePath,ProcessId,WindowsVersion,CommandLine

C:\> wmic.exe PATH Win32_Process GET Caption,Name,OSName,ExecutablePath,ProcessId,WindowsVersion,ParentProcessId,SessionId,CommandLine
```

## 3.2 - Spawn Process

```
C:\> wmic.exe PROCESS CALL CREATE "<process>.exe"
```

## 3.3 - Fork Background Process

```
C:\> start /b <command> [arguments]
```

---
## References

### Mubix

- [Malicious.link: Get Process List](https://room362.com/posts/2020/get-process-list/)
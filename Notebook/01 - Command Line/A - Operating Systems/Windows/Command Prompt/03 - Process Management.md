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
C:\> wmic.exe process list brief

C:\> wmic.exe PATH Win32_Process GET Caption, Processid, Commandline

C:\> wmic.exe PATH Win32_Process GET Caption,Name,OSName,ExecutablePath,ProcessId,WindowsVersion,CommandLine

C:\> wmic.exe PATH Win32_Process GET Caption,Name,OSName,ExecutablePath,ProcessId,WindowsVersion,ParentProcessId,SessionId,CommandLine
```

## 3.2 - Spawn Process

```
C:\> wmic.exe PROCESS CALL CREATE "<process>.exe"
```

## 3.3 - Terminate Processes

### 3.3.1 - Kill Process

Terminate the process with process identifier (PID).

```
C:\> taskkill.exe /pid <PID> /f
```

Terminate the process with a name.

```
C:\> taskkill.exe /im <process.exe> /f

C:\> wmic.exe PROCESS WHERE "Name LIKE '<process.exe>'" CALL Terminate
```

## 3.4 - Fork Background Process

```
C:\> start /b <command> [arguments]
```

---
## References

### Backlinks

- [[Windows Command Prompt References]]

### LOFLCAB

- [LOFLCAB: tasklist](https://lofl-project.github.io/loflcab/Binaries/tasklist/)

- [LOFLCAB: taskkill](https://lofl-project.github.io/loflcab/Binaries/taskkill/)

- [LOFLCAB: WMIC](https://lofl-project.github.io/loflcab/Binaries/wmic/)

### Hacking Articles

- [Hacking Articles: Post Exploitation Using WMIC (System Command)](https://www.hackingarticles.in/post-exploitation-using-wmic-system-command/)

### Mubix

- [Malicious.link: Get Process List](https://room362.com/posts/2020/get-process-list/)
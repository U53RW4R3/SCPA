# 04 - Process Manipulation

Search Tag(s): #havoc #command-and-control #interactive-shell

## 4.1 - Help Menu

```
Demon » help proc

 - Command       :  proc
 - Description   :  process enumeration and management
 - Usage         :  proc [command]
 - Example       :  proc list

  Command                        Description
  ---------                      -------------
  list                           displays a list of running processes on the target
  kill                           kills the process from specified PID
  blockdll                       block non microsoft signed dlls
  create                         create a process
  modules                        lists loaded modules/dlls from a remote process
  grep                           grep information from the specified remote process
  memory                         query for memory regions
  find-module                    query for processes with specified loaded module
```

## 4.2 - Create Process

```
Demon » proc create notepad.exe

Demon » proc create taskmgr.exe
```

## 4.3 - Terminate Process

```
Demon » proc kill <pid>
```

## 4.4 - Inject Process

### 4.4.1 - Shellcode

Inject shellcode through a process identifier.

```
Demon » shellcode inject <x64 | x86> <pid> /path/to/shellcode.bin
```

Inject shellcode to spawn a new implant.

```
Demon » shellcode spawn <x64 | x86> /path/to/shellcode.bin
```

### 4.4.2 - Configure Spawn Process

Configure a path to spawn new process when executing commands through the demon agent.

```
Demon » config inject.spawn64 C:\Windows\System32\rundll32.exe

Demon » config inject.spawn32 C:\Windows\System32\rundll32.exe
```

### 4.4.3 - Spawn DLL

Inject DLL file through a process identifier.

```
Demon » dll inject <pid> /path/to/local/file.dll [arguments]
```

Inject DLL file to spawn a new implant.

```
Demon » dll spawn /path/to/local/file.dll [arguments]
```

### 4.4.4 - DotNET CLR Assembly

List dotnet versions in a current system.

```
Demon » dotnet list-versions
```

Execute .NET files through memory in the current process.

```
Demon » dotnet inline-execute /path/to/local/dotnet_file.exe [arguments]
```

### 4.4.5 - Object File

Execute object file through memory in the current process.

```
Demon » inline-execute /path/to/objectfile.o [arguments]
```
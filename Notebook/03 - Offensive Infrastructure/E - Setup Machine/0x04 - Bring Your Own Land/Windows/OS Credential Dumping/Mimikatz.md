# Mimikatz

## 01 - Installation

### 1.1 - Command Prompt

Download the archive.

```
C:\> curl.exe -O https://github.com/gentilkiwi/mimikatz/releases/download/2.2.0-20220919/mimikatz_trunk.zip

C:\> certutil.exe -urlcache -split -f https://github.com/gentilkiwi/mimikatz/releases/download/2.2.0-20220919/mimikatz_trunk.zip mimikatz_trunk.zip
```

Extract it then delete it.

```
C:\> tar.exe xf .\mimikatz_trunk.zip
del /f .\mimikatz_trunk.zip
```

### 1.2 - PowerShell

```
PS C:\> Invoke-WebRequest -UseBasicParsing -Uri https://github.com/gentilkiwi/mimikatz/releases/download/2.2.0-20220919/mimikatz_trunk.zip -OutFile mimikatz_trunk.zip
Expand-Archive .\mimikatz_trunk.zip
Remove-Item -Force .\mimikatz_trunk.zip
```

## 02 - Help Menu

```
C:\> cd .\mimikatz_trunk\x64
.\mimikatz.exe
```

TODO: Copy and paste the help menu for mimikatz

```
mimikatz # ::
```
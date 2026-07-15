# PrivescCheck

## 01 - Installation

### 1.1 - Fileless Memory

```
PS C:\> iex (New-Object Net.WebClient).DownloadString('https://github.com/itm4n/PrivescCheck/releases/latest/download/PrivescCheck.ps1')
```

### 1.2 - Dropper

#### 1.2.1 - Command Prompt

Download the file on disk.

```
C:\> certutil.exe -urlcache -split -f https://github.com/itm4n/PrivescCheck/releases/latest/download/PrivescCheck.ps1 PrivescCheck.ps1

C:\> certutil.exe -urlcache -split -f https://github.com/itm4n/PrivescCheck/releases/latest/download/PrivescCheck.ps1 PrivescCheck.ps1

C:\> curl.exe -O https://github.com/itm4n/PrivescCheck/releases/latest/download/PrivescCheck.ps1

C:\> curl.exe -O https://github.com/itm4n/PrivescCheck/releases/latest/download/PrivescCheck.ps1
```

#### 1.2.2 - PowerShell

```
PS C:\> Invoke-WebRequest -UseBasicParse -Uri https://github.com/itm4n/PrivescCheck/releases/latest/download/PrivescCheck.ps1 -OutFile PrivescCheck.ps1
```

## 02 - Import Module

```
PS C:\> Set-ExecutionPolicy Bypass -Scope Process -Force

PS C:\> Import-Module .\PrivescCheck.ps1
```

---
## References

### Source Repositories

- [PrivescCheck](https://github.com/itm4n/PrivescCheck)
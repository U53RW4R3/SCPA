# OpenSSL

## Installation

### EXE

Download the installer in command prompt.

```
C:\> certutil.exe -urlcache -split -f https://slproweb.com/download/Win64OpenSSL_Light-3_6_0.exe Win64OpenSSL_Light-3_6_0.exe

C:\> curl.exe -sO https://slproweb.com/download/Win64OpenSSL_Light-3_6_0.exe
```

Download the installer in PowerShell cmdlet.

```
PS C:\> Invoke-WebRequest -Uri https://slproweb.com/download/Win64OpenSSL_Light-3_6_0.exe -OutFile Win64OpenSSL_Light-3_6_0.exe
```

Silently install the software.

```
C:\> .\Win64OpenSSL-3_6_0_Light.exe /VERYSILENT /SP- /NORESTART [/DIR="C:\OpenSSL-Project"]
```

### MSI

```
C:\> msiexec.exe /i /qn /norestart https://slproweb.com/download/Win64OpenSSL_Light-3_6_0.msi
```

---
## References

### OpenSSL

- [Shining Light Productions: Win32OpenSSL](https://slproweb.com/products/Win32OpenSSL.html)
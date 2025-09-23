# Powerless

## 01 - Installation

### 1.1 - Command Prompt

Download the file on disk.

```
C:\> certutil -urlcache -split -f https://github.com/gladiatx0r/Powerless/raw/refs/heads/master/Powerless.bat Powerless.bat

C:\> certutil -urlcache -split -f https://raw.githubusercontent.com/gladiatx0r/Powerless/master/Powerless.bat Powerless.bat

C:\> curl -O https://github.com/gladiatx0r/Powerless/raw/refs/heads/master/Powerless.bat

C:\> curl -O https://raw.githubusercontent.com/gladiatx0r/Powerless/master/Powerless.bat Powerless.bat
```

### 1.2 - PowerShell

```
PS C:\> Invoke-WebRequest -UseBasicParse -Uri https://github.com/gladiatx0r/Powerless/raw/refs/heads/master/Powerless.bat -OutFile Powerless.bat

PS C:\> Invoke-WebRequest -UseBasicParse -Uri https://raw.githubusercontent.com/gladiatx0r/Powerless/master/Powerless.bat -OutFile Powerless.bat
```

---
## References

### Source Repositories

- [Powerless](https://github.com/gladiatx0r/Powerless)
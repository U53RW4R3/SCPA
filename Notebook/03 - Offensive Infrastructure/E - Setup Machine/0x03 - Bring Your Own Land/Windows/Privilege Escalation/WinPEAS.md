# WinPEAS

> [!INFO]
> There are 3 programs made in different programming languages and they are C#, batch and PowerShell.

## 01 - Compile DotNET

Install a targeting pack from this [link](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481). Then compile `WinPEAS`.

TODO: figure it out how to manually compile WinPEAS in C#

```
C:\> git clone https://github.com/carlospolop/PEASS-ng.git

C:\> cd PEASS-ng\winPEAS\winPEASexe\winPEAS

C:\PEASS-ng\winPEAS\winPEASexe\winPEAS> copy Program.cs Program.cs.bak

C:\PEASS-ng\winPEAS\winPEASexe\winPEAS> dotnet new console --force

C:\PEASS-ng\winPEAS\winPEASexe\winPEAS> dotnet add package Microsoft.VisualStudio.UnitTesting --version 11.0.50727.1

C:\PEASS-ng\winPEAS\winPEASexe\winPEAS> del Program.cs; move Program.cs.bak Program.cs
```

_**I'm still having an error**_

```
C:\PEASS-ng\winPEAS\winPEASexe\winPEAS> dotnet build -c Release -p:TargetFrameworkVersion=v4.8.1
```

---
## References

### Source Repositories

- [WinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS)

- [WinPEAS Metasploit Module](https://github.com/carlospolop/PEASS-ng/tree/master/metasploit)
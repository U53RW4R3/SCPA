# Manual

## 01 - OLE Object

TODO: Include screenshots

In Microsoft Word it has a OLE Object that serves as an alternative to macros. Go to **Insert** > **Object** > **Create From File**. Choose the file you've created which is the payload of batch script such as `payload.bat`.

Then click **Display as icon** then click on **Browse** to choose any custom icon. If your windows architecture system is 64-bit. Browse all the way to `C:\Program Files\Microsoft Office\Office16\` then choose any of the icons that ends with a"`.EXE` (I choose `EXCEL.EXE` in my case) then after you've chose the icon of your choice rename the caption to `ReadMe.xlsx` or `Report Sales.xlsx`.

Now right click on the crafted OLE Object. **Go to Packager Shell Object Object** > **Properties**. You can finally see that the file has been attached. Provide the instructions to tell the target (the victim) to double click on the OLE Object in a deceiving way.

A few improvements that can be made to deceive the victim. Instead of naming `payload.bat` or `launch.bat`. Give it a less obvious file name such as `Sales.bat` or something that is depending on the context of your social engineering vector.

### 1.1 - Shortcut Link

TODO: Fill this information

```

```

## 02 - DDE

In Microsoft Word to insert the payload press **CTRL+F9** then copy the payload between the curly brackets (`{ }`).

---
## References

### Github

- [TrustedSec: auto_SettingContent-ms](https://github.com/trustedsec/auto_SettingContent-ms)

### Red Team Notes

- [Red Team Notes: Phishing OLE Object LNK](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-ole-+-lnk)

- [Red Team Notes: Embedded HTML Forms](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-embedded-html-forms)

- [Red Team Notes: Embedded Internet Explorer](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-embedded-internet-explorer)

- [Red Team Notes: Phishing DDE](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/t1173-dde)

### Null Byte

- [Null Byte: How to Execute Code in a Microsoft Word Document Without Security Warnings](https://null-byte.wonderhowto.com/how-to/execute-code-microsoft-word-document-without-security-warnings-0180495/)

### DMCXBlue

- [DMCXBlue: Attachments - Dynamic Data Exchange](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-dynamic-data-exchange)

- [DMCXBlue: Dynamic Data Exchange](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/execution/t1559-inter-process-communication/dynamic-data-exchange)
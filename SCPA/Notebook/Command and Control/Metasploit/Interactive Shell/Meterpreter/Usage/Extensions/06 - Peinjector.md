# 06 - Peinjector

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

## 6.1 - Help Menu

```
meterpreter > load peinjector

Peinjector Commands
===================

    Command       Description
    -------       -----------
    injectpe      Inject a shellcode into a given executable

Unhook Commands
===============

    Command       Description
    -------       -----------
    unhook_pe     Unhook the current process
    
    
meterpreter > unhook_pe -h
Usage: unhook_pe

Removes any runtime hooks placed by PSPs

OPTIONS:

    -h  Help banner
```

## 6.2 - Unhook Runtime

```
meterpreter > unhook_pe
[+] Command execution completed:
[0, 0, nil]
```

## 6.3 - Inject Shellcode

TODO: Fill this info

```
meterpreter > injectpe
```
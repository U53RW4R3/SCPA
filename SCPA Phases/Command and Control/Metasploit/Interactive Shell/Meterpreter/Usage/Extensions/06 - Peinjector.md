# 06 - Peinjector

Search Tags: #metasploit-framework #command-and-control

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

## 6.2 - Usage

* **Unhook the API**

```
meterpreter > unhook_pe
[+] Command execution completed:
[0, 0, nil]
```
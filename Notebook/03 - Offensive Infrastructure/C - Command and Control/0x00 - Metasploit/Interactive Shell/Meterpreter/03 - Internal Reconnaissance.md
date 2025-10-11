# 03 - Internal Reconnaissance

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

```
meterpreter > help

Core Commands
=============

    Command                   Description
    -------                   -----------

    bgkill                    Kills a background meterpreter script
    bglist                    Lists running background scripts

    disable_unicode_encoding  Disables encoding of unicode strings
    enable_unicode_encoding   Enables encoding of unicode strings

    guid                      Get the session GUID

    set_timeouts              Set the current session timeout values
    sleep                     Force Meterpreter to go quiet, then re-establish session
    ssl_verify                Modify the SSL certificate verification setting
    transport                 Manage the transport mechanisms

Stdapi: System Commands
=======================

    Command       Description
    -------       -----------

    reboot        Reboots the remote computer

    shutdown      Shuts down the remote computer

    suspend       Suspends or resumes a list of processes

```

## 3.1 - System

Retrieve UUID

```
meterpreter > uuid
```

Get current session ID

```
meterpreter > machine_id
```

## 3.3 - Networking

Route

```
meterpreter > route -h
Usage: route [-h] command [args]

Display or modify the routing table on the remote machine.

Supported commands:

   add    [subnet] [netmask] [gateway]
   delete [subnet] [netmask] [gateway]
   list



OPTIONS:

    -h  Help banner.
```
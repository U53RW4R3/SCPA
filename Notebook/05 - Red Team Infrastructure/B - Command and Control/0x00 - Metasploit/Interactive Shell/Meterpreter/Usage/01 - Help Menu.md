# 01 - Help Menu

Search Tag(s): #metasploit-framework #command-and-control #help-menu

```
meterpreter > help

Core Commands
=============

    Command                   Description
    -------                   -----------

    bgkill                    Kills a background meterpreter script
    bglist                    Lists running background scripts
    bgrun                     Executes a meterpreter script as a background thread
    channel                   Displays information or control active channels
    close                     Closes a channel
    detach                    Detach the meterpreter session (for http/https)
    disable_unicode_encoding  Disables encoding of unicode strings
    enable_unicode_encoding   Enables encoding of unicode strings

    get_timeouts              Get the current session timeout values
    guid                      Get the session GUID


    pivot                     Manage pivot listeners
    pry                       Open the Pry debugger on the current session
    quit                      Terminate the meterpreter session
    read                      Reads data from a channel

    set_timeouts              Set the current session timeout values
    sleep                     Force Meterpreter to go quiet, then re-establish session
    ssl_verify                Modify the SSL certificate verification setting
    transport                 Manage the transport mechanisms

    uuid                      Get the UUID for the current session
    write                     Writes data to a channel


Stdapi: System Commands
=======================

    Command       Description
    -------       -----------

    drop_token    Relinquishes any active impersonation token.

    localtime     Displays the target system local date and time

    reboot        Reboots the remote computer

    shutdown      Shuts down the remote computer

    suspend       Suspends or resumes a list of processes

```
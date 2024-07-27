# 03 - ExtAPI

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

TODO: Provide usage examples

## 3.1 - Help Menu

```
meterpreter > load extapi

Extapi: Window Management Commands
==================================

    Command       Description
    -------       -----------
    window_enum   Enumerate all current open windows


Extapi: Service Management Commands
===================================

    Command          Description
    -------          -----------
    service_control  Control a single service (start/pause/resume/stop/restart)
    service_enum     Enumerate all registered Windows services
    service_query    Query more detail about a specific Windows service


Extapi: Clipboard Management Commands
=====================================

    Command                   Description
    -------                   -----------
    clipboard_get_data        Read the target's current clipboard (text, files, images)
    clipboard_monitor_dump    Dump all captured clipboard content
    clipboard_monitor_pause   Pause the active clipboard monitor
    clipboard_monitor_purge   Delete all captured clipboard content without dumping it
    clipboard_monitor_resume  Resume the paused clipboard monitor
    clipboard_monitor_start   Start the clipboard monitor
    clipboard_monitor_stop    Stop the clipboard monitor
    clipboard_set_text        Write text to the target's clipboard


Extapi: ADSI Management Commands
================================

    Command                      Description
    -------                      -----------
    adsi_computer_enum           Enumerate all computers on the specified domain.
    adsi_dc_enum                 Enumerate all domain controllers on the specified domain.
    adsi_domain_query            Enumerate all objects on the specified domain that match a filter.
    adsi_group_enum              Enumerate all groups on the specified domain.
    adsi_nested_group_user_enum  Recursively enumerate users who are effectively members of the group specified.
    adsi_user_enum               Enumerate all users on the specified domain.


Extapi: WMI Querying Commands
=============================

    Command       Description
    -------       -----------
    wmi_query     Perform a generic WMI query and return the results
```

---
## References

- [OJ's Perspective: 3 Months of Meterpreter](https://buffered.io/posts/3-months-of-meterpreter/)
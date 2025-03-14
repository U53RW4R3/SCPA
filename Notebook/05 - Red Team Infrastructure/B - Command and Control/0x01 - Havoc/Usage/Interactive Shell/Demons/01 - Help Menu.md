---
author(s):
  - Userware
tags:
---
# 01 - Help Menu

Search Tag(s): #havoc #command-and-control #interactive-shell #help-menu

```
Demon » help

Demon Commands
==============

  Command                  Type         Description
  -------                  -------      -----------
  adcs_enum                Command      Enumerate CAs and templates in the AD using Win32 functions
  adcs_request             Command      Request an enrollment certificate
  adduser                  Command      Add a new user to a machine.
  addusertogroup           Command      Add the specified user to the specified group
  arp                      Command      Lists out ARP table
  bofbelt                  Command      A Seatbelt port using BOFs
  cacls                    Command      List user permissions for the specified file, wildcards supported
  cat                      Command      display content of the specified file
  cd                       Command      change to specified directory

  config                   Module       configure the behaviour of the demon session
  cp                       Command      copy file from one location to another
  dcenum                   Command      enumerate domain information using Active Directory Domain Services
  dir                      Command      list specified directory
  dll                      Module       dll spawn and injection modules
  domainenum               Command      Lists users accounts in the current domain
  dotnet                   Module       execute and manage dotnet assemblies

  driversigs               Command      checks drivers for known edr vendor names
  enableuser               Command      Activates (and if necessary enables) the specified user account on the target computer.
  enum_filter_driver       Command      Enumerate filter drivers
  enumlocalsessions        Command      Enumerate currently attached user sessions both local and over RDP
  env                      Command      Print environment variables.
  exit                     Command      cleanup and exit
  get-asrep                Command      Enumerate a given domain for user accounts with ASREP.
  get-delegation           Command      Enumerate a given domain for different types of abusable Kerberos Delegation settings.
  get-netsession           Command      Enumerate sessions on the local or specified computer
  get-spns                 Command      Enumerate a given domain for user accounts with SPNs.
  get_password_policy      Command      Gets a server or DC's configured password policy
  help                     Command      Shows help message of specified command
  inline-execute           Command      executes an object file

  job                      Module       job manager
  jump-exec                Module       lateral movement module
  kerberoast               Command      perform Kerberoasting against specified SPN
  klist                    Command      list Kerberos tickets
  ldapsearch               Command      Execute LDAP searches (NOTE: specify *,ntsecuritydescriptor as attribute parameter if you want all attributes + base64 encoded ACL of the objects, this can then be resolved using BOFHound. Could possibly break pagination, although everything seemed fine during testing.)
  listdns                  Command      lists dns cache entries
  locale                   Command      Prints locale information
  luid                     Command      get current logon ID

  mv                       Command      move file from one location to another
  nanodump                 Command      Dump the LSASS process
  nanodump_ppl_dump        Command      Bypass PPL and dump LSASS
  nanodump_ppl_medic       Command      Bypass PPL and dump LSASS
  nanodump_ssp             Command      Load a Security Support Provider (SSP) into LSASS
  net                      Module       network and host enumeration module
  netGroupList             Command      List groups from the default or specified domain
  netGroupListMembers      Command      List group members from the default or specified domain
  netLclGrpLstMmbrs        Command      List local group members from the local or specified group
  netLocalGroupList        Command      List local groups from the local or specified computer
  netshares                Command      List shares on local or remote computer
  netsharesAdmin           Command      List shares on local or remote computer and gets more info then standard netshares (requires admin)

  netuptime                Command      Returns information about the boot time on the local (or a remote) machine
  netuser                  Command      Get info about specific user. Pull from domain if a domainname is specified
  netview                  Command      lists local workstations and servers
  nslookup                 Command      Make a DNS query. DNS server is the server you want to query (do not specify or 0 for default). Record type is something like A, AAAA, or ANY
  pivot                    Module       pivoting module
  powerpick                Command      executes unmanaged powershell commands
  powershell               Command      executes powershell.exe commands and gets the output
  proc                     Module       process enumeration and management
  ptt                      Command      import Kerberos ticket into a logon session
  purge                    Command      purge a Kerberos ticket
  pwd                      Command      get current directory
  quser                    Command      Simple implementation of quser.exe using the Windows API
  reg_delete               Command      Deletes the registry key or value
  reg_query                Command      Query a registry value or enumerate a single key
  reg_query_recursive      Command      Recursively enumerate a key starting at path
  reg_save                 Command      Saves the registry path and all subkeys to disk
  reg_set                  Command      This command creates or sets the specified registry key (or value) on the target host.
  remove                   Command      remove file or directory
  resources                Command      list available memory and space on the primary disk drive
  routeprint               Command      prints ipv4 routes on the machine
  rportfwd                 Module       reverse port forwarding
  samdump                  Command      Dump the SAM, SECURITY and SYSTEM registries
  sc_create                Command      This command creates a service on the target host.
  sc_delete                Command      This command deletes the specified service on the target host.
  sc_description           Command      This command sets the description of an existing service on the target host.
  sc_enum                  Command      Enumerate services for qc, query, qfailure, and qtriggers info
  sc_qc                    Command      sc qc impelmentation in BOF
  sc_qdescription          Command      Queries a services description
  sc_qfailure              Command      Query a service for failure conditions
  sc_qtriggerinfo          Command      Query a service for trigger conditions
  sc_query                 Command      sc query implementation in BOF
  sc_start                 Command      This command starts the specified service on the target host.
  sc_stop                  Command      This command stops the specified service on the target host.
  schtasksenum             Command      Enumerate scheduled tasks on the local or remote computer
  schtasksquery            Command      Query the given task on the local or remote computer
  screenshot               Command      takes a screenshot
  sessions                 Command      get logon sessions
  setuserpass              Command      Sets the password for the specified user account on the target computer.
  shell                    Command      executes cmd.exe commands and gets the output
  shellcode                Module       shellcode injection techniques
  sleep                    Command      sets the delay to sleep
  socks                    Module       socks5 proxy
  task                     Module       task manager
  tasklist                 Command      This command displays a list of currently running processes on either a local or remote machine.
  tgtdeleg                 Command      retrieve a usable TGT for the current user
  token                    Module       token manipulation and impersonation
  transfer                 Command      download transfer module
  upload                   Command      uploads a specified file
  uptime                   Command      lists system boot time
  userenum                 Command      Lists user accounts on the current computer
  whoami                   Command      get the info from whoami /all without starting cmd.exe
  windowlist               Command      list windows visible on the users desktop
  wmi_query                Command      Run a wmi query and display results in CSV format
```
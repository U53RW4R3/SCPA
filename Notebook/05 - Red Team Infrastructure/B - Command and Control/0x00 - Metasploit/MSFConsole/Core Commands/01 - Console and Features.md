# 01 - Console and Features

## 1.2 - Colors

```
msf > color enabled
```

## 1.1 - Console Prompt

| Variables | Description                        |
| --------- | ---------------------------------- |
| `%clr`    | Reset the color to default.        |
| `%whi`    | White color.                       |
| `%grn`    | Green color.                       |
| `%blu`    | Blue color.                        |
| `%blk`    | Black color.                       |
| `%red`    | Red color.                         |
| `%yel`    | Yellow color.                      |
| `%cya`    | Cyan color.                        |
| `%mag`    | Magenta color.                     |
| `%bld`    | Bold font.                         |
| `%D`      | Current local directory.           |
| `%H`      | Host name.                         |
| `%J`      | Current number of jobs running.    |
| `%L`      | Local IP address.                  |
| `%S`      | Currently number of sessions open. |
| `%T`      | Time stamp.                        |
| `%U`      | Username.                          |

Modify the `Prompt`.

```
msf > setg Prompt [%grnmsf%clr](%yelJobs%clr:%whi%J%clr %cyaAgents%clr:%whi%S%clr)
```

Modify the `MeterpreterPrompt`.

```
msf > setg MeterpreterPrompt (%grnMeterpreter %bld%blu%S%clr)(%whi%D%clr)
```

Modify the `PromptChar`.

```
msf > setg PromptChar %bld%whi>>%cl
```

You can append the configuration (`config`) in metasploit's home directory.

```
cat > /root/.msf4/config << EOF
[framework/core]
Prompt=[%grnmsf%clr](%yelJobs%clr:%whi%J%clr %cyaAgents%clr:%whi%S%clr)
PromptChar=%bld%whi>>%clr
MeterpreterPrompt=(%grnMeterpreter %bld%blu%S%clr)(%whi%D%clr)
EOF
```

## 1.2 - Features

```
msf > features

msf > get

msf > getg
```

## 1.3 - History

Show a brief history of commands.

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

Show a specific history with a number.

```
msf > history -n <number>
```

Show all of the history commands

```
msf > history -a
```

Clear history commands.

```
msf > history -c
[+] Command history and history file cleared
```

---
## References

### Mubix

- [Mubix: MSFConsole Prompt Fiddling](https://malicious.link/posts/2011/2011-10-09-msfconsole-prompt-fiddling/)
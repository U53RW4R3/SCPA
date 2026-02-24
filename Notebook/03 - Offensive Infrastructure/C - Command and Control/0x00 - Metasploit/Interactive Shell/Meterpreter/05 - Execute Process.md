# 05 - Execute Process

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

## 03 - Source Script

Execute a local shell script file on remote machine. `y` represent execute the script in background, `n` represent on foreground

```
source /path/to/local/commands.sh <y | n>
```

## 5.1 - Help Menu

```
meterpreter > execute -h
Usage: execute -f file [options]
Executes a command on the remote machine.

OPTIONS:

    -a   The arguments to pass to the command.
    -c   Channelized I/O (required for interaction).
    -d   The 'dummy' executable to launch when using -m.
    -f   The executable command to run.
    -h   Help menu.
    -H   Create the process hidden from view.
    -i   Interact with the process after creating it.
    -k   Execute process on the meterpreters current desktop
    -m   Execute from memory.
    -p   Execute process in a pty (if available on target platform)
    -s   Execute process in a given session as the session user
    -t   Execute process with currently impersonated thread token
    -z   Execute process in a subshell
```

## 2.7 - Channels

```
meterpreter > channel -h
Usage: channel [options]

Displays information about active channels.

OPTIONS:

    -c   Close the given channel.
    -h   Help menu.
    -i   Interact with the given channel.
    -k   Close the given channel.
    -K   Close all channels.
    -l   List active channels.
    -r   Read from the given channel.
    -w   Write to the given channel.
```

List active channels.

```
meterpreter > channel -l

    Id  Class  Type
    --  -----  ----
    7   3      stdapi_process
    8   3      stdapi_process
    9   3      stdapi_process
    10  3      stdapi_process
    11  3      stdapi_process
    12  3      stdapi_process
    13  3      stdapi_process
    14  3      stdapi_process
    16  3      stdapi_process
    17  3      stdapi_process
    18  3      stdapi_process
    19  3      stdapi_process
```

Spawn the command prompt then interact it manually using `channel`.

```
meterpreter > execute -Hcf cmd.exe

meterpreter > channel -i <channel_ID>
```

Spawn the command prompt.

```
meterpreter > execute -Hcf cmd.exe
```

Then insert commands to a specific `channel` ID.

```
meterpreter > channel -w <channel_ID>
Enter data followed by a '.' on a empty line:

whoami.exe
ping.exe -n 1 127.0.0.1
.
[*] Wrote <bytes> bytes to channel <channel_ID>
```

```
meterpreter > write <channel_ID>
Enter data followed by a '.' on a empty line:

whoami.exe
ping.exe -n 1 127.0.0.1
.
[*] Wrote <bytes> bytes to channel <channel_ID>
```

Then print the output instead of doing it interactively.

```
meterpreter > channel -r <channel_ID>
Read <bytes> bytes from <channel_ID>:
```

```
meterpreter > read <channel_ID>
Read <bytes> bytes from <channel_ID>:
```

Terminate a specific channel ID.

```
meterpreter > channel -k <channel_ID>
```

Terminate all channels.

```
meterpreter > channel -K
Killing all channels...
Killed all channels.
```

```
close                     Closes a channel
```

## Timeouts

```
meterpreter > get_timeouts
Session Expiry  : @ 2022-05-21 17:23:58
Comm Timeout    : 300 seconds
Retry Total Time: 3600 seconds
Retry Wait Time : 10 seconds
```
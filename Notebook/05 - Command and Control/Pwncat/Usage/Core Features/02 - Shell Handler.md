# 02 - Shell Handler

## 2.1 - Reverse Callback Shell

```
$ pwncat-cs -m <linux | windows> -lp <PORT>

$ pwncat-cs -m <linux | windows> [IP]:<PORT>
```

## 2.2 - Bind Callback Shell

- Regular bind shells

```
$ pwncat-cs -m <linux | windows> connect://<target_IP>:<target_PORT>

$ pwncat-cs -m <linux | windows> <target_IP>:<target_PORT>

$ pwncat-cs -m <linux | windows> <target_IP> <target_PORT>
```

- Connect via SSH

```
$ pwncat-cs [ssh://]<username>:<password>@<target_IP>:<target_PORT>

$ pwncat-cs [-i /path/to/ssh_key] <username>@<target_IP>:<target_PORT>

$ pwncat-cs [-i /path/to/ssh_key] -p [<target_PORT>] <username>@<target_IP>
```
# #pwncat-vl

## 01 - Shell Handler

### 1.1 - Reverse Callback Shell

```
$ pwncat-vl -m <linux | windows> -lp <PORT>

$ pwncat-vl -m <linux | windows> [IP]:<PORT>
```

> [!INFO] This Only Works with TLS Payloads
> Using TLS to encrypt commands when the implant transmits along it's capability.

```
$ pwncat-vl -m <linux | windows> -lp <PORT> --ssl [--ssl-cert /path/to/certificate.pem --ssl-key /path/to/key.pem]

$ pwncat-vl -m <linux | windows> [IP]:<PORT> --ssl [--ssl-cert /path/to/certificate.pem --ssl-key /path/to/key.pem]
```

### 1.2 - Bind Callback Shell

Regular bind shells

```
$ pwncat-vl -m <linux | windows> connect://<target_IP>:<target_PORT>

$ pwncat-vl -m <linux | windows> <target_IP>:<target_PORT>

$ pwncat-vl -m <linux | windows> <target_IP> <target_PORT>
```

Connect via SSH

```
$ pwncat-vl [ssh://]<username>:<password>@<target_IP>:<target_PORT>

$ pwncat-vl [-i /path/to/ssh_key] <username>@<target_IP>:<target_PORT>

$ pwncat-vl [-i /path/to/ssh_key] -p [<target_PORT>] <username>@<target_IP>
```

## 02 - Reconnecting with Implants

### 2.1 - Reconnect Callback Shell

```
$ pwncat-vl [reconnect://]<username>@<target_IP>

$ pwncat-vl reconnect://<username>@<host_id>
```

### 2.2 - List Active Implants

```
$ pwncat-vl --list
```

## 03 - Resource File

```
$ pwncat-vl -c /path/to/pwncatrc
```

Create a resource file to automate post-exploitation process.

```
# Set your remote hosts file
set -g lhost "127.0.0.1"
# Set your command prefix
set -g prefix c-k
# Set the default private key to use for privilege escalation
set -g privkey "data/pwncat"
# Set the pwncat backdoor user and password
set -g backdoor_user "pwncat"
set -g backdoor_pass "pwncat"
set -g db "file://db/pwncat"

set -g on_load {
	# Run a command upon a stable connection
	# privesc -l
}

# Examples of command bindings
bind s "sync"
bind c "set state command"

# Create aliases for commands
alias up upload
alias down download
alias clear "local clear"
alias cls "local clear"

# Shortcuts allow single-character prefix which indicate the entire command
# string be passed as the arguments to a specific command. For example:
# "!ls" run "local ls" given the below directives
shortcut ! local
shortcut @ run
```
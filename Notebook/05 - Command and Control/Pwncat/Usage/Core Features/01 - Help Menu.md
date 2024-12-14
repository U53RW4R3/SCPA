# 01 - Help Menu

```
$ pwncat-cs -h
usage: pwncat-cs [-h] [--version] [--download-plugins] [--config CONFIG] [--ssl] [--ssl-cert SSL_CERT] [--ssl-key SSL_KEY] [--identity IDENTITY] [--listen] [--platform PLATFORM] [--port PORT]
                 [--list] [--verbose]
                 [[protocol://][user[:password]@][host][:port]] [port]

Start interactive pwncat session and optionally connect to existing victim via a known platform and channel type. This entrypoint can also be used to list known implants on previous targets.

positional arguments:
  [protocol://][user[:password]@][host][:port]
                        Connection string describing victim
  port                  Alternative port number to support netcat-style syntax

options:
  -h, --help            show this help message and exit
  --version, -v         Show version number and exit
  --download-plugins    Pre-download all Windows builtin plugins and exit immediately
  --config CONFIG, -c CONFIG
                        Custom configuration file (default: ./pwncatrc)
  --ssl                 Connect or listen with SSL
  --ssl-cert SSL_CERT   Certificate for SSL-encrypted listeners (PEM)
  --ssl-key SSL_KEY     Key for SSL-encrypted listeners (PEM)
  --identity IDENTITY, -i IDENTITY
                        Private key for SSH authentication
  --listen, -l          Enable the `bind` protocol (supports netcat-style syntax)
  --platform PLATFORM, -m PLATFORM
                        Name of the platform to use (default: linux)
  --port PORT, -p PORT  Alternative way to specify port to support netcat-style syntax
  --list                List installed implants with remote connection capability
  --verbose, -V         Enable verbose output for the remote commands executed by `pwncat`
```

---
## References

- [Calebstewart Pwncat](https://github.com/calebstewart/pwncat)
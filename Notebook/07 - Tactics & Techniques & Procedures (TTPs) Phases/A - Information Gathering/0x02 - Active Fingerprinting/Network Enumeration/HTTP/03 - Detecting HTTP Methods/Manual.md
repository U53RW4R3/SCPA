# Manual

## 01 - cURL

```
$ curl -i -X OPTIONS http://<IP>/path/to/url

$ curl -k -i -X OPTIONS https://<IP>/path/to/url
```

## 02 - Netcat

```
$ nc <IP> <PORT>
OPTIONS http[s]://<IP> HTTP/1.1
```
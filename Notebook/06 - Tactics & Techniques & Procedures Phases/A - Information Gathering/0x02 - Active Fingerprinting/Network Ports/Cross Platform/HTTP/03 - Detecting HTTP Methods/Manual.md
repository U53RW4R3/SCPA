---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - curl
---
# Manual

## 01 - #curl

```
$ curl -i -X OPTIONS http://<IP>/path/to/url

$ curl -k -i -X OPTIONS https://<IP>/path/to/url
```

## 02 - #netcat

```
$ nc <IP> <PORT>
OPTIONS http[s]://<IP> HTTP/1.1
```
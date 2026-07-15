# Security Search Engines

## 01 - Null Authentication

Shodan dorks.

```
port:5900,5901 authentication disabled

RFB 003.008 authentication disabled
```

## 02 - Insecure VNC

Shodan dorks.

```
port:5900,5901 has_screenshot:true

product:VNC has_screenshot:true

port:5900,5901 product:VNC has_screenshot:true
```
# Establish connection via TOR

## 01 - cURL

`$ curl -sL --socks 127.0.0.1:9050 --socks5-hostname 127.0.0.1:9050 http://<onion_URL>`

## 02 - Socat

```
$ socat TCP4-LISTEN:<local_port>,reuseaddr,fork SOCKS4A:127.0.0.1:<onion_URL_without_scheme>:80,socksport=9050

$ curl -s http://127.0.0.1:<local_port>
```

---
## References

- [NetEye: Analysis of a Dark Web site](https://www.neteye-blog.com/2021/07/analysis-of-a-dark-web-site/)
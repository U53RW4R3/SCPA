---
author(s):
  - Userware
tags:
  - operation-security
  - anonymization
  - tor
---
# Establish Connection via TOR

## 01 - #curl 

```
$ curl -sL --socks 127.0.0.1:9050 --socks5-hostname 127.0.0.1:9050 http://<onion_URL>
```

## 02 - #socat

The syntax as it follows.

```
$ socat TCP4-LISTEN:<local_PORT>,reuseaddr,fork SOCKS4A:127.0.0.1:<onion_hostname>:80,socksport=9050
```

You can use the script to make your life easier.

![[03 - Helpers#^9aa75c|Socat bash script]]

Just specify the listening port.

```
$ ./pivotbinder.sh -v 2 -l <local_PORT> -r <onion_hostname> -b 80
```

Then interact the web server using `curl` to check if it works.

```
$ curl -s http://127.0.0.1:<local_port>
```

---
## References

### NetEye

- [NetEye: Analysis of a Dark Web site](https://www.neteye-blog.com/2021/07/analysis-of-a-dark-web-site/)
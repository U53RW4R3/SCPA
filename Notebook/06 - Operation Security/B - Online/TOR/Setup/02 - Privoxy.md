# 02 - Privoxy

```
$ sudo cat > /etc/privoxy/config << EOF
user-manual /usr/share/doc/privoxy/user-manual/
confdir /etc/privoxy
logdir /var/log/privoxy
actionsfile match-all.action # Actions that are applied to all sites and maybe overruled later on.
actionsfile default.action   # Main actions file
actionsfile user.action      # User customizations
#actionsfile regression-tests.action     # Tests for privoxy-regression-test
filterfile default.filter
filterfile user.filter      # User customizations
logfile logfile
listen-address  127.0.0.1:8118
enable-remote-toggle  0
enable-remote-http-toggle  0
enable-edit-actions 0
enforce-blocks 0
buffer-limit 4096
enable-proxy-authentication-forwarding 0
forwarded-connect-retries  0
accept-intercepted-requests 0
allow-cgi-request-crunching 0
split-large-forms 0
keep-alive-timeout 5
tolerate-pipelining 1
socket-timeout 300
forward-socks4  /   127.0.0.1:9050  .
forward-socks4a /   127.0.0.1:9050  .
forward-socks5  /   127.0.0.1:9050  .
EOF

$ privoxy /etc/privoxy/config
```

Refer to [[Terminal Setup]] section to configure a bash resource file

```
$ proxy_on
username:
server: localhost
port: 8118
```

Lookup IP

```
$ curl https://ipinfo.io

$ curl https://ifconfig.me

$ curl https://ip.me

$ curl 'https://api.ipify.org?format=json'

$ curl https://ipecho.net/plain
```

Check if you're connected to TOR

```
$ curl -s https://check.torproject.org/api/ip | jq -r .IsTor

$ curl -s https://check.torproject.org | grep -m 1 "Congratulations. This browser is configured to use Tor."
```

---
## References

### Check TOR Circuit

- [Check TOR](https://check.torproject.org/)

### Lookup IP

- [Ifconfig.me](https://ifconfig.me/)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [IPAPI](https://ipapi.co)

- [Amazon AWS IP Lookup](https://checkip.amazonaws.com)

- [IP API](https://ip-api.com)

- [IPv4.cat](https://about.ipv4.cat/)

- [IP Echo Service](https://ipecho.net)
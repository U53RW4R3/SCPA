# SOCKS Proxy Servers

## 01- Scoop

### 1.1 - Compile binary

```
$ git clone https://git.tcp.direct/perp/scoop.git && \
cd scoop && \
go build scoop.go
```

- Fetch SOCKS Proxy servers

`$ ./scrape && ./scoop`

### 1.2 - Use Proxychains

`$ cat socks5.conf`

---

```
strict_chain  
proxy_dns  
tcp_read_time_out 15000  
tcp_connect_time_out 8000  
localnet 127.0.0.1/255.255.255.255  
[ProxyList]  
socks5  127.0.0.1 9999 user pass
```

`$ proxychains -f socks5.conf curl https://ipinfo.io`

### 1.3 - Use Privoxy

`$ cat /etc/privoxy/config`

---

```
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
forward-socks5  /       user:pass@127.0.0.1:9999  .
```

`$ privoxy /etc/privoxy/config`

Refer to [[Terminal Setup]] section to configure a bash resource file

```
$ proxy_on
username:
server: localhost
port: 8118
```

## 02 - Proxychains

TODO: Merge them together for the script and add an option for sqlmap

`$ cat socks5.conf`

---

```
strict_chain
proxy_dns
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.1/255.255.255.255
[ProxyList]
socks4  <IP> <PORT>
socks5  <IP> <PORT> [username] [password]
http    <IP> <PORT> [username] [password]
```

Refer to [[Proxychains|proxychains]] under Pivoting SOCKS proxy section



## 03 - Privoxy

`$ cat /etc/privoxy/config`

---

```
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
forward-socks5  /   <username>:<password>@<IP>:<PORT>  .
```

`$ privoxy /etc/privoxy/config`

Refer to [[Terminal Setup]] section to configure a bash resource file

```
$ proxy_on
username:
server: localhost
port: 8118
```

`$ curl https://ipinfo.io`

---
## References

- [Scoop](https://git.tcp.direct/perp/scoop)
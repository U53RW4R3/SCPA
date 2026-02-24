# Configure Proxies

## 01- Scoop

### 1.1 - Compile binary

```
$ git clone https://git.tcp.direct/perp/scoop.git && \
cd scoop && \
go build scoop.go
```

Fetch SOCKS Proxy servers

```
$ ./scrape && ./scoop
```

### 1.2 - [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Post Exploitation/Pivoting/Linux/Proxychains|Proxychains]]

A configuration file template to setup `proxychains-ng`.

```
$ cat > socks5.conf << EOF
strict_chain  
proxy_dns  
tcp_read_time_out 15000  
tcp_connect_time_out 8000  
localnet 127.0.0.1/255.255.255.255  
[ProxyList]  
socks5  127.0.0.1 9999 user pass
EOF
```

Specify the configuration file to use `proxychains-ng`.

```
$ proxychains -f socks5.conf curl https://ipinfo.io
```

### 1.3 - [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Post Exploitation/Pivoting/Linux/Privoxy|Privoxy]]

```
$ cat > privoxy_config << EOF
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
EOF
```

Specify the configuration file to use `privoxy`.

```
$ privoxy /etc/privoxy/config
```

Refer to [[Terminal Setup]] section to configure a bash resource file

```
$ proxy_on
username:
server: localhost
port: 8118
```

## 02 - [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Post Exploitation/Pivoting/Linux/Proxychains|Proxychains]]

Refer to [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x05 - Pivot/Linux/SOCKS Proxy/Proxychains|proxychains]] under Pivoting SOCKS proxy section.

```
$ cat > socks5.conf << EOF
strict_chain
proxy_dns
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.1/255.255.255.255
[ProxyList]
socks4  <IP> <PORT>
socks5  <IP> <PORT> [username] [password]
http    <IP> <PORT> [username] [password]
EOF
```

## 03 - [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Post Exploitation/Pivoting/Linux/Privoxy|Privoxy]]

```
$ cat > /etc/privoxy/config << EOF
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
EOF

$ privoxy /etc/privoxy/config
```

^0a4669

Refer to [[Terminal Setup]] section to configure a bash resource file

```
$ proxy_on
username:
server: localhost
port: 8118
```

Then check the IP address.

```
$ curl https://ipinfo.io
```

---
## References

### Source Repositories

- [Scoop](https://git.tcp.direct/perp/scoop)
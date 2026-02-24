# Use Cases

## 01 - SSH

### 1.1 - SSH inbound rule connection

```
$ sudo iptables -A INPUT -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```

### 1.2 - SSH outbound rule connection

```
$ sudo iptables -A OUTPUT -p tcp -o <interface> -m state --state ESTABLISHED,RELATED -j ACCEPT
```
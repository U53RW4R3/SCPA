---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - redirectors
---
# Redirectors

## 01 - Linux

### 1.1 - `socat`

Linux redirector

```
root@redirector:~# socat TCP4-LISTEN:<redirector_PORT>,fork TCP4:<bind_C2_IP>:443 &

root@redirector:~# iptables -I INPUT -p tcp -m tcp --dport <redirector_PORT> -j ACCEPT

root@redirector:~# iptables -t nat -A PREROUTING -p tcp --dport <redirector_PORT> -j DNAT -–to-destination <bind_C2_IP>:443

root@redirector:~# iptables -t nat -A POSTROUTING -j MASQUERADE

root@redirector:~# iptables -I FORWARD -j ACCEPT

root@redirector:~# iptables -P FORWARD ACCEPT

root@redirector:~# sysctl net.ipv4.ip_forward=1
```

Command and Control

```
root@c2server:~# iptables -A INPUT -p tcp -s <redirector_IP> --dport 443 -j ACCEPT

root@c2server:~# iptables -A OUTPUT -p tcp -d <redirector_IP> --dport 443 -j ACCEPT

root@c2server:~# iptables -A INPUT -p tcp --dport 443 -j DROP

root@c2server:~# iptables -A OUTPUT -p tcp --dport 443 -j DROP
```

## 02 - Windows

### 2.1 - `netsh.exe`

Windows redirector

```
C:\> netsh.exe interface portproxy add v4tov4 listenport=<redirector_PORT> listenaddress=<redirector_IP> connectport=<bind_C2_PORT> connectaddress=<bind_C2_IP>

C:\> netsh.exe advfirewall firewall add rule name="Relay Port <PORT>" dir=in action=allow protocol=tcp localport=<redirector_PORT>
```

Command and Control

```
root@c2server:~# iptables -A INPUT -p tcp -s <redirector_IP> --dport <redirector_PORT> -j ACCEPT

root@c2server:~# iptables -A OUTPUT -p tcp -d <redirector_IP> --dport <redirector_PORT> -j ACCEPT

root@c2server:~# iptables -A INPUT -p tcp --dport <redirector_PORT> -j DROP

root@c2server:~# iptables -A OUTPUT -p tcp --dport <redirector_PORT> -j DROP
```

---
## References

- [advania: Reducing The Indicators of Compromise (IOCs) on Beacon and Team Server](https://www.advania.co.uk/insights/blog/reducing-the-indicators-of-compromise-iocs-on-beacon-and-team-server/)

- [Hardening For Your C&C](https://medium.com/void-security/the-red-fortress-hardening-for-your-c-c-9c06af8147bd)

- [Nginx for Red Teams](https://0xda.de/blog/2020/02/nginx-for-red-teams/)
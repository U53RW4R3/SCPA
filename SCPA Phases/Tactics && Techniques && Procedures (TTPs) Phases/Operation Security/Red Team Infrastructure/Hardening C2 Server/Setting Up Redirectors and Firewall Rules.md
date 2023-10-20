# Setting Up Redirectors and Firewall Rules

Search Tag: #red-team-infrastructure

## 01 - Linux

### 1.1 - Socat

```
root@redirector:~# socat TCP4-LISTEN:433,fork TCP4:<C2_IP>:443 &

root@redirector:~# iptables -I INPUT -p tcp -m tcp –dport 443 -j ACCEPT

root@redirector:~# iptables -t nat -A PREROUTING -p tcp –dport 443 -j DNAT -–to-destination <C2_IP>:443

root@redirector:~# iptables -t nat -A POSTROUTING -j MASQUERADE

root@redirector:~# iptables -I FORWARD -j ACCEPT

root@redirector:~# iptables -P FORWARD ACCEPT

root@redirector:~# sysctl net.ipv4.ip_forward=1
```

```
root@c2server:~# iptables -A INPUT -p tcp -s <redirector_IP> --dport 443 -j ACCEPT

root@c2server:~# iptables -A OUTPUT -p tcp -d <redirector_IP> --dport 443 -j ACCEPT

root@c2server:~# iptables -A INPUT -p tcp --dport 443 -j DROP

root@c2server:~# iptables -A OUTPUT -p tcp --dport 443 -j DROP
```
## 02 - Windows

### 2.1 - Netsh

```
C:\> netsh interface portproxy add v4tov4 listenport=443 listenaddress=<redirector_IP> connectport=443 connectaddress=<C2_IP>

C:\> netsh advfirewall firewall add rule name="Relay Port <PORT>" dir=in action=allow protocol=tcp localport=443
```

```
root@c2server:~# iptables -A INPUT -p tcp -s <redirector_IP> --dport 443 -j ACCEPT

root@c2server:~# iptables -A OUTPUT -p tcp -d <redirector_IP> --dport 443 -j ACCEPT

root@c2server:~# iptables -A INPUT -p tcp --dport 443 -j DROP

root@c2server:~# iptables -A OUTPUT -p tcp --dport 443 -j DROP
```

---
## References

- [Hardening For Your C&C](https://medium.com/void-security/the-red-fortress-hardening-for-your-c-c-9c06af8147bd)

- [Nginx for Red Teams](https://0xda.de/blog/2020/02/nginx-for-red-teams/)
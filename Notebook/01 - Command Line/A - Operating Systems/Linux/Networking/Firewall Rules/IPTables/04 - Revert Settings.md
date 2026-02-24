# 04 - Revert Settings

Delete curent rules and chains in `iptables`

```
# iptables --flush
iptables --delete-chain
```

Revert back default policies.

```
# iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```
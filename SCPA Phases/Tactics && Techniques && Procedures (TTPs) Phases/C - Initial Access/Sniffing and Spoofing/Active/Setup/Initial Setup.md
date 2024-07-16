# Initial Setup

## Enable IP forwarding

```
# cat /proc/sys/net/ipv4/ip_forward
0
# echo 1 > /proc/sys/net/ipv4/ip_forward
```

`$ sudo sysctl -w net.ipv4.ip_forward=1`
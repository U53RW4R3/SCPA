# 07 - Miscellaneous

Search Tags(s): #active-reconnaissance #port-scanners #network-mapper

## 7.1 - Aggressive scan


> [!NOTE]
> This is an equivalent to these switches `nmap -O -sVC --traceroute <IP>`.

```
$ sudo nmap -A <IP>
```

List the network interfaces.

```
$ nmap --iflist
```
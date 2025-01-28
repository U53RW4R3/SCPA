# PfSense

## System Requirements

- Storage 16 GB
- RAM 1GB
- 1 Core of Processor

## ISO Files

ISO file: [https://atxfiles.netgate.com/mirror/downloads/](https://atxfiles.netgate.com/mirror/downloads/)  
  
This [link](https://atxfiles.netgate.com/mirror/downloads/pfSense-CE-2.7.0-RELEASE-amd64.iso.gz) is only when you want to setup for after authentication when the attacker able to get retrieve or use default credentials using a vulnerability scanner like `nuclei` for example. An authenticated command injection in the web user interface using `commix` will get the job done. Read more [here](https://docs.netgate.com/downloads/pfSense-SA-23_10.webgui.asc).

## Network Settings

### Hypervisor Configuration

TODO: Fill in the missing information

```
192.168.56.2 - 192.168.56.254
```

`<insert_image>`

### Router Configuration

`<insert_image>`

## Internet Connection

### Ping

Check for internet connection using to ping host from the router.

```
Enter an option: 7

Enter a host name or IP address: www.google.com
```

DHCP server has already assigned an IP address.

```
$ ip address show eth0

$ ip route 
default via 192.168.56.1 dev eth0 proto dhcp src 192.168.56.101 metric 100 
192.168.56.0/24 dev eth0 proto kernel scope link src 192.168.56.101 metric 100

$ ping -c 192.168.56.1
PING 192.168.56.1 (192.168.56.1) 56(84) bytes of data.
64 bytes from 192.168.56.1: icmp_seq=1 ttl=64 time=0.319 ms

--- 192.168.56.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.319/0.319/0.319/0.000 ms
```

If you see this that's because you've chose the **Host-only Adapter**. It's great for isolating the network. Revert back to **Internal Network** instead.

```
$ ping -c 1 google.com
ping: google.com: Temporary failure in name resolution
```

### Web browser

So we have to configure it on the web browser. Enter the address of the router gateway IP address. Confirm with nmap to check the http port is open.

`<insert_image>`

#### Exceptions when network configuration is different

So the gateway is `192.168.56.100` it's because we've setup with the start client of `.100`. if you run `ip route` to check the gateway. The port scanner provides proof otherwise.

```
$ nmap -Pn 192.168.56.100
..[omitted]..
Nmap scan report for 192.168.56.100
Host is up (0.00036s latency).
Not shown: 998 filterred tcp ports (no-response)
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 17.87 seconds
```

## Configuration

Open your web browser to navigate the router gateway using the URL above. The default credentials are `admin:pfsense`.

`<insert_image>`

New password will be `Password123!`.
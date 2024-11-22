# 03 - Whonix

## 3.1 - Hypervisor Type 2

### 3.1.1 - VirtualBox

Select the virtual machine and click on **Settings**.

![[01 - VM VirtualBox Manager Settings.png]]

Change **NAT** to **Internal Network**

![[02 - VM VirtualBox Manager Network.png]]

You're all set user!

![[03 - VM VirtualBox Manager Adapter.png]]

### 3.1.2 - Network Settings

#### 3.1.2.1 - Command Line

Disable the default network adapter.

```
# ifdown enp7s0

# ifdown eth0
```

Remove the default DNS configuration and include the Whonix IP as the DNS gateway.

```
# chattr -i /etc/resolv.conf

# cat > /etc/resolv.conf << EOF
nameserver 10.152.152.10
EOF

# chattr +i /etc/resolv.conf
```

Specify the network configuration to route the virtual network of the TOR gateway.

```
# INTERFACE=eth0
cat > /etc/network/interfaces/ << EOF
auto lo
iface lo net loopback
iface $INTERFACE inet static
		address 10.152.152.<change_THIS>
		netmask 255.255.192.0
		gateway 10.152.152.10
EOF
```

Enable the default network adapter.

```
# ifup enp7s0

# ifup eth0
```

#### 3.1.2.2 - Graphical User Interface

Depending on your **DE (Desktop Environment)** on GNU/Linux search for anything related to **Network Configuration Settings**.

![[01 - Advanced Network Configuration XFCE.png]]

Click the **plus** icon.

![[02 - Network Connections XFCE.png]]

Choose **Ethernet**.

![[03 - Network Connection Type XFCE.png]]

Go to IPv4 Settings and enter the following details from this table below.

| Address          | Netmask             | Gateway       | DNS servers   |
| ---------------- | ------------------- | ------------- | ------------- |
| 10.152.152.2-254 | 255.255.192.0 or 18 | 10.152.152.10 | 10.152.152.10 |

Here's an image as an example.

![[04 - VM VirtualBox Manager Adapter Settings.png]]

---
## References

### Whonix

- [Whonix](https://www.whonix.org/)

- [adrelanos: VPN-Firewall](https://github.com/adrelanos/VPN-Firewall)

### Configure Whonix Gateway

- [VEEXH: How To Safely Access The Darknet For Threat Research](https://medium.com/the-sleuth-sheet/how-to-safely-access-the-darknet-for-threat-research-89047bfc3cbb)

- [Vasileiadis A. (CyberKid): Complete anonymity on Kali Linux using Tor, Whonix and VPN](https://medium.com/@redfanatic7/complete-anonymity-on-kali-linux-using-tor-whonix-and-vpn-16cf9aa2ebdc)

- [Jerome: Force VirtualBox VMs to use Tor](https://fr33tux.org/post/redirect-vm-to-tor/)

### Check TOR Circuit

- [Check TOR](https://check.torproject.org/)

### Lookup IP

- [Ifconfig.me](https://ifconfig.me/)

- [IP.me](https://ip.me/)

- [IPInfo](https://ipinfo.io)

- [Amazon AWS IP Lookup](https://checkip.amazonaws.com)

- [IP API](https://ip-api.com)

- [IPv4.cat](https://about.ipv4.cat/)
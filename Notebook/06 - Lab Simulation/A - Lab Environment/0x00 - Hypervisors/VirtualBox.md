# VirtualBox

## Internal Network

### Router

TODO: Insert images

### Hypervisor's Builtin DHCP Server

```
> VBoxManage dhcpserver add --network="LAN Network" --server-ip=192.168.56.1 --lower-ip=192.168.56.2 --upper-ip=192.168.56.30 --netmask=255.255.255.0 --enable
```
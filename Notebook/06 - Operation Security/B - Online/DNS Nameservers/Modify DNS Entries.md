# Modify DNS Entries

Refer to the list of [[06 - Operation Security/B - Online/DNS Nameservers/Helpers|DNS nameservers]].

## DHCP Client

```
# cat > /etc/dhcp/dhclient.conf << EOF
prepend domain-name-servers <dns_nameserver_1>, <dns_nameserver_2>, <dns_nameserver_3>;

request subnet-mask, broadcast-address, time-offset, routers,
		domain-name, domain-search, host-name,
		root-path, interface-mtu;
EOF
```

## `resolvconf`

```
# systemctl enable resolvconf.service
```

```
# cat > /etc/resolvconf/resolv.conf.d/base
208.67.222.222
208.67.220.220
1.1.1.1
```

```
# echo "dns-nameservers 208.67.222.222 208.67.220.220 1.1.1.1" >> /etc/network/interfaces
```

```
# cat > /etc/resolv.conf
208.67.222.222
208.67.220.220
1.1.1.1
```

```
# systemctl restart resolvconf.service
```

Restart the network daemon service.

```
# systemctl restart NetworkManager
```

---
## References

### DNS Leak Test

- [DNS Leak Test](https://dnsleaktest.com)

### Browser Leaks

- [Browser Leaks](https://browserleaks.com/ip)
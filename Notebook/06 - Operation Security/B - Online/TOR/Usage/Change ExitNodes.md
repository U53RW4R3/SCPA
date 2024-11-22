# Change ExitNodes

## 01 - TOR Config Files

It is found system wide in `/etc/tor/torrc` and the other location `/usr/local/etc/torrc.d/50_user.conf` is for [[03 - Whonix|whonix]] gateway.

## 02 - Change Static IP and/or country code

You can either modify config file to an IP address or a country code.

```
ExitNode <static_TOR_IP>
ExitNode {<country_code>}
```

---
## References

- [platformcosmo: Tor IP Addresses](https://github.com/platformcosmo/Tor-IP-Addresses)
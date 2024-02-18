# Change ExitNodes

- The global `torrc` and the second line is for [[03 - Whonix|whonix]] gateway.

```
/etc/tor/torrc
/usr/local/etc/torrc.d/50_user.conf
```

- You can either modify config file to an IP address or a country code.

```
ExitNode <static_TOR_IP>
ExitNode {<country_code>}
```
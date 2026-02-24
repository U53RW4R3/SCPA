# Configure Whonix

## Setup SSH Server

> [!WARNING]
> These actions are not recommended by the Whonix team itself for security reasons.

![[Host-only Adapter.png]]

Install the required packages.

```
# apt install -y openssh-server isc-dhcp-client
```

Enable SSH server.

```
# systemctl enable --now ssh
```

Configure the network interface for control by editing the file `/etc/network/interfaces.d/30_non-qubes-whonix`. Add the line to the end of it.

```
auto eth2
iface eth2 inet dhcp
```

Configure Whonix Firewall. In the `/etc/whonix_firewall.d` directory.

```
# cp /etc/whonix_firewall.d/30_whonix_gateway_default.conf /etc/whonix_firewall.d/50_user.conf
```

Uncomment the line in `/etc/whonix_firewall.d/50_user.conf` configuration file.

```
EXTERNAL_OPEN_PORTS+=" 22 "
```

Uncomment another the line.

```
EXT_IF="eth0"
```

Then run `ip address` to see the network interface `vboxnet0`.

```
EXT_IF="eth0 eth2"
```

Refresh the [[04 - Operation Security/A - Offline/Computer Settings/Troubleshooting/Linux|IP address]] without rebooting the machine.

```
# dhclient -v eth2
```
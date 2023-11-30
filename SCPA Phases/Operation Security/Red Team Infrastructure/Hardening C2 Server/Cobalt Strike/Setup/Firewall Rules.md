# Firewall Rules

```
# mkdir /etc/iptables
# iptables -I INPUT 1 -p tcp -s 0.0.0.0/0 --dport 50050 -j DROP
# iptables -I INPUT 1 -p tcp -s 127.0.0.1 --dport 50050 -j ACCEPT
# iptables-save > /etc/iptables/rules.v4
```

- A script to autorun after reboot. Run this as root (without `sudo`)

```bash
cat << EOF > /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo iptables-restore < /etc/iptables/rules.v4

exit 0
EOF
```

```
$ sudo chmod 755 /etc/rc.local

$ sudo systemctl start rc-local
```
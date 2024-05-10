# RDP

## 01 - Setup

Install the X11 RDP server.

`$ sudo apt install -y xrdp`

Edit the configuration file.

```
$ sudo nano /etc/xrdp/xrdp.ini
[globals]
..[snip]..
address=0.0.0.0
```

Restart the RDP server.

`$ sudo systemctl restart xrdp`
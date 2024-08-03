# RDP

## 01 - Linux Setup

Install the X11 RDP server.

```
$ sudo apt install -y xrdp
```

Edit the configuration file.

```
$ sudo nano /etc/xrdp/xrdp.ini
[globals]
..[truncated]..
address=0.0.0.0
```

Restart the RDP server.

```
$ sudo systemctl restart xrdp
```
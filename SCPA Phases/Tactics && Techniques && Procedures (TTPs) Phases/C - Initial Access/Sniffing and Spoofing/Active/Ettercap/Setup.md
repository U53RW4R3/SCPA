# Setup

## 01 - Install Dependencies

```
$ sudo apt-get install build-essential debhelper bison check cmake flex groff \
      ghostscript libbsd-dev libcurl4-openssl-dev libgeoip-dev libltdl-dev \
      libmaxminddb-dev libgtk-3-dev libltdl-dev libluajit-5.1-dev \
      libncurses5-dev libnet1-dev libpcap-dev libpcre2-dev libpcre3-dev libssl-dev
```

## 02 - Install Ettercap

### 2.1 - Compile from Source

Download the tarball git release.

```
$ wget https://github.com/Ettercap/ettercap/releases/download/v0.8.3.1/ettercap-0.8.3.1.tar.gz && \
tar xzf ettercap-0.8.3.1.tar.gz && cd ettercap-0.8.3.1/ && \
mkdir build && cd build && \
cmake -DCMAKE_BUILD_TYPE=Debug -DENABLE_IPV6=On .. && \
make && sudo make install
```

Clone the source repository.

```
$ git clone https://github.com/Ettercap/ettercap && cd ettercap && \
mkdir build && cd build && \
cmake -DCMAKE_BUILD_TYPE=Debug -DENABLE_IPV6=On .. && \
make && sudo make install
```

### 2.2 - Package Manager

Ettercap GUI.

```
$ sudo apt install -y ettercap-graphical
```

Just ettercap CLI.

```
$ sudo apt install -y ettercap-text-only
```

## 03 - Modify ettercap privileges and uncommon firewall redirections

```
$ sudo cat /etc/ettercap/etter.conf
[privs]
ec_uid = 0                # nobody is the default
ec_gid = 0                # nobody is the default
..[truncated]..
   redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp -d %destination --dport %port -j REDIRECT --to-port %rport"
   redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp -d %destination --dport %port -j REDIRECT --to-port %rport"
```

## 04 - Troubleshooting

### 4.1 - Uninstall Ettercap from compiled source

```
$ sudo make uninstall
```

---
## References

- [Ettercap](https://github.com/Ettercap/ettercap)
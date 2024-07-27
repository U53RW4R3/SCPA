# 06 - Connect

Search Tag(s): #metasploit-framework #command-and-control

## 6.1 - Help Menu

```
msf > connect -h
Usage: connect [options] <host> <port>

Communicate with a host, similar to interacting via netcat, taking advantage of
any configured session pivoting.

OPTIONS:

    -c, --comm <comm>               Specify which Comm to use.
    -C, --crlf                      Try to use CRLF for EOL sequence.
    -h, --help                      Help banner.
    -i, --send-contents <file>      Send the contents of a file.
    -p, --proxies <proxies>         List of proxies to use.
    -P, --source-port <port>        Specify source port.
    -S, --source-address <address>  Specify source address.
    -s, --ssl                       Connect with SSL.
    -u, --udp                       Switch to a UDP socket.
    -w, --timeout <seconds>         Specify connect timeout.
    -z, --try-connection            Just try to connect, then return.
```

## 6.2 - Usage

```
msf > connect <IP> <PORT>

msf > connect -s <IP> <PORT>
```

---
## References

- [Metasploit Unleashed: Msfconsole Commands](https://www.offsec.com/metasploit-unleashed/msfconsole-commands/)
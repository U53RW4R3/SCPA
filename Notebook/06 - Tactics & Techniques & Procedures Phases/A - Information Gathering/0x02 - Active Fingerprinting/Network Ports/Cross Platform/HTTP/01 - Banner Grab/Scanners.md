# Scanners

## 01 - Network Mapper

```
$ sudo nmap -p 80,443,8000,8080,8443 -Pn -n -sV <IP>
```

## 02 - [[Nikto|Nikto]]

```
$ nikto -host <IP> -Display V -findonly

$ nikto -host <IP> -Display V -Plugins headers
```

## 03 - Metasploit

```
msf > use auxiliary/scanner/http/http_version

msf auxiliary(scanner/http/http_version) > options

Module options (auxiliary/scanner/http/http_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   THREADS  1                yes       The number of concurrent threads (max one per host)
   VHOST                     no        HTTP server virtual host


View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/http_version) > set threads 8

msf auxiliary(scanner/http/http_version) > set rhosts <target_IP>

msf auxiliary(scanner/http/http_version) > run
```

TODO: Docker HTTP version

```
msf > use auxiliary/scanner/http/docker_version
```
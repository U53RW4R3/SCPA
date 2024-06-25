# Metasploit

- Metasploit auxiliary module HTTP WebDAV Internal IP Scanner

```
msf > use auxiliary/scanner/http/webdav_internal_ip

msf auxiliary(scanner/http/webdav_internal_ip) > options

Module options (auxiliary/scanner/http/webdav_internal_ip):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   PATH     /                yes       Path to use
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   THREADS  1                yes       The number of concurrent threads (max one per host)
   VHOST                     no        HTTP server virtual host


View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/webdav_internal_ip) > set path </uri_path>

msf auxiliary(scanner/http/webdav_internal_ip) > set threads 8

msf auxiliary(scanner/http/webdav_internal_ip) > set rhosts <IP>

msf auxiliary(scanner/http/webdav_internal_ip) > set rport <PORT>

msf auxiliary(scanner/http/webdav_internal_ip) > run
```
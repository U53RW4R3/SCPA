# Metasploit

- **Metasploit auxiliary module Generic HTTP Directory Traversal Utility**

```
msf > use auxiliary/scanner/http/http_traversal

msf auxiliary(scanner/http/http_traversal) > options 

Module options (auxiliary/scanner/http/http_traversal):  
  
  Name      Current Setting                                     Required  Description  
  ----      ---------------                                     --------  -----------  
  DATA                                                          no        HTTP body data  
  DEPTH     5                                                   yes       Traversal depth  
  FILELIST  /opt/metasploit/data/wordlists/sensitive_files.txt  yes       Wordlist file to brute force  
  METHOD    GET                                                 yes       HTTP Request Method (Accepted: GET, POST, HEAD, PUT)  
  PATH      /                                                   yes       Vulnerable path. Ex: /foo/index.php?pg=  
  PATTERN   ^HTTP/\d\.\d 200                                    yes       Regexp pattern to determine directory traversal  
  Proxies                                                       no        A proxy chain of format type:host:port[,type:host:port][...]  
  RHOSTS                                                        yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html  
  RPORT     80                                                  yes       The target port (TCP)  
  SSL       false                                               no        Negotiate SSL/TLS for outgoing connections  
  THREADS   1                                                   yes       The number of concurrent threads (max one per host)  
  VHOST                                                         no        HTTP server virtual host  
  
  
Auxiliary action:  
  
  Name   Description  
  ----   -----------  
  CHECK  Check for basic directory traversal  
  
  
  
View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/http_traversal) > set action <CHECK | DOWNLOAD | PHPSOURCE | WRITABLE>

msf auxiliary(scanner/http/http_traversal) > set path </uri_path>

msf auxiliary(scanner/http/http_traversal) > set filelist </path/to/wordlist.txt>

msf auxiliary(scanner/http/http_traversal) > set method <GET | POST | HEAD | PUT>

msf auxiliary(scanner/http/http_traversal) > set pattern <regex>

msf auxiliary(scanner/http/http_traversal) > set depth <int>

msf auxiliary(scanner/http/http_traversal) > set threads 8

msf auxiliary(scanner/http/http_traversal) > set rhosts <IP>

msf auxiliary(scanner/http/http_traversal) > set rport <PORT>

msf auxiliary(scanner/http/http_traversal) > run
```
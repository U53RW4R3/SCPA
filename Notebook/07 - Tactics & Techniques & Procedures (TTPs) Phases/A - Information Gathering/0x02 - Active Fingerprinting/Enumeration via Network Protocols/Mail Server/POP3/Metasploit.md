# Metasploit

## 01 - Banner Grab

```
msf > use auxiliary/scanner/pop3/pop3_version

msf auxiliary(scanner/pop3/pop3_version) > options

Module options (auxiliary/scanner/pop3/pop3_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    110              yes       The target port (TCP) 
   THREADS  1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/pop3/pop3_version) > set rhosts <IP>

msf auxiliary(scanner/pop3/pop3_version) > set threads 4

msf auxiliary(scanner/pop3/pop3_version) > run -j
```
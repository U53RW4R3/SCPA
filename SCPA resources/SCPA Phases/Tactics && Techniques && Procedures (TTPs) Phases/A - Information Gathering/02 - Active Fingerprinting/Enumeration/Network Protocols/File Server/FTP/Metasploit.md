# Metasploit

## 01 - Banner Grab

```
msf > use auxiliary/scanner/ftp/ftp_version

msf auxiliary(scanner/ftp/ftp_version) > options

Module options (auxiliary/scanner/ftp/ftp_version):

   Name     Current Setting      Required  Description 
   ----     ---------------      --------  ----------- 
   FTPPASS  mozilla@example.com  no        The password for the specified username 
   FTPUSER  anonymous            no        The username to authenticate as 
   RHOSTS                        yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    21                   yes       The target port (TCP) 
   THREADS  1                    yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/ftp/ftp_version) > set rhosts <IP>

msf auxiliary(scanner/ftp/ftp_version) > set threads 8

msf auxiliary(scanner/ftp/ftp_version) > run
```
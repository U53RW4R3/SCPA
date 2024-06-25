# Metasploit
## 01 - Banner Grab

```
msf > use auxiliary/scanner/smb/smb_version

msf auxiliary(scanner/smb/smb_version) > options

Module options (auxiliary/scanner/smb/smb_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   THREADS  1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smb/smb_version) > set rhosts <IP>

msf auxiliary(scanner/smb/smb_version) > set threads 5

msf auxiliary(scanner/smb/smb_version) > run -j
```
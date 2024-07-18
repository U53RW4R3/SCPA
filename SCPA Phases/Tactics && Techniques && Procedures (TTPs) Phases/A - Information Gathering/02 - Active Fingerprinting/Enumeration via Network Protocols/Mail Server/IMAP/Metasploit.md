# Metasploit

## 01 - Banner Grab

```
msf > use auxiliary/scanner/imap/imap_version

msf auxiliary(scanner/imap/imap_version) > options

Module options (auxiliary/scanner/imap/imap_version):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   IMAPPASS                   no        The password for the specified username
   IMAPUSER                   no        The username to authenticate as
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     143              yes       The target port (TCP)
   THREADS   1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/imap/imap_version) > set rhosts <IP>

msf auxiliary(scanner/imap/imap_version) > set threads 4

msf auxiliary(scanner/imap/imap_version) > set imapuser <username>

msf auxiliary(scanner/imap/imap_version) > set imappass <password>

msf auxiliary(scanner/imap/imap_version) > exploit -j
```
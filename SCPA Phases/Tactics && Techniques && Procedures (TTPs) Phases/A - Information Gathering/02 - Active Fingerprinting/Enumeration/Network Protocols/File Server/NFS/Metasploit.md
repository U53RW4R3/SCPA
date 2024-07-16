# Metasploit

```
msf > use auxiliary/scanner/nfs/nfsmount

msf auxiliary(scanner/nfs/nfsmount) > options

Module options (auxiliary/scanner/nfs/nfsmount):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   PROTOCOL  udp              yes       The protocol to use (Accepted: udp, tcp)
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     111              yes       The target port (TCP)
   THREADS   1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/nfs/nfsmount) > set protocol <udp | tcp>

msf auxiliary(scanner/nfs/nfsmount) > set rhosts <IP>

msf auxiliary(scanner/nfs/nfsmount) > set rport <PORT>

msf auxiliary(scanner/nfs/nfsmount) > set threads 2

msf auxiliary(scanner/nfs/nfsmount) > run
```
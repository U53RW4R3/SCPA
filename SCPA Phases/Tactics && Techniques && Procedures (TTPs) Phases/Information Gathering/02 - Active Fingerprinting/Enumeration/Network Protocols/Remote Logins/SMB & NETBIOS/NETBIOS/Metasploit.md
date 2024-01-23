# Metasploit

- Metasploit auxiliary module to enumerate NetBIOS

```
msf > use auxiliary/scanner/netbios/nbname

msf auxiliary(scanner/netbios/nbname) > options

Module options (auxiliary/scanner/netbios/nbname):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to probe in each set
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      137              yes       The target port (UDP)
   THREADS    10               yes       The number of concurrent threads

msf auxiliary(scanner/netbios/nbname) > set rhosts <IP>

msf auxiliary(scanner/netbios/nbname) > run -j
```
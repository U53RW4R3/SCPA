# Metasploit

- Metasploit auxilary module HTTP SSL Certificate Checker

```
msf > use auxiliary/scanner/http/cert

msf auxiliary(scanner/http/cert) > options

Module options (auxiliary/scanner/http/cert):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   ISSUER   .*               yes       Show a warning if the Issuer doesn't match this regex
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    443              yes       The target port (TCP)
   SHOWALL  false            no        Show all certificates (issuer,time) regardless of match
   THREADS  1                yes       The number of concurrent threads (max one per host)


View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/cert) > set issuer <regex>

msf auxiliary(scanner/http/cert) > set threads 8

msf auxiliary(scanner/http/cert) > set rhosts <IP>

msf auxiliary(scanner/http/cert) > set rport <PORT>

msf auxiliary(scanner/http/cert) > run
```

- Metasploit auxilary module SSL/TLS Version Detection

```
msf > use auxiliary/scanner/ssl/ssl_version

Module options (auxiliary/scanner/ssl/ssl_version):  
  
  Name        Current Setting  Required  Description  
  ----        ---------------  --------  -----------  
  RHOSTS                       yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html  
  RPORT       443              yes       The target port (TCP)  
  SSLCipher   All              yes       SSL cipher to test (Accepted: All, TLS_AES_256_GCM_SHA384, TLS_CHACHA20_POLY1305_SHA256, TLS_AES_128_GCM_SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-RSA-AES256-GCM-SHA384, DHE-DSS-AES256-GCM-SHA384, DHE-RSA-AES256-GCM-SHA384, ECDHE-ECDSA-CHACHA20-POLY1305, ECDHE-RSA-CHAC  
                                         HA20-POLY1305, DHE-RSA-CHACHA20-POLY1305, ECDHE-ECDSA-AES256-CCM8, ECDHE-ECDSA-AES256-CCM, DHE-RSA-AES256-CCM8, DHE-RSA-AES256-CCM, ECDHE-ECDSA-ARIA256-GCM-SHA384, ECDHE-ARIA256-GCM-SHA384, DHE-DSS-ARIA256-GCM-SHA384, DHE-RSA-ARIA256-GCM-SHA384, ADH-AES256-GCM-SHA384, ECD  
                                         HE-ECDSA-AES128-GCM-SHA256, ECDHE-RSA-AES128-GCM-SHA256, DHE-DSS-AES128-GCM-SHA256, DHE-RSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES128-CCM8, ECDHE-ECDSA-AES128-CCM, DHE-RSA-AES128-CCM8, DHE-RSA-AES128-CCM, ECDHE-ECDSA-ARIA128-GCM-SHA256, ECDHE-ARIA128-GCM-SHA256, DHE-DSS-ARIA1  
                                         28-GCM-SHA256, DHE-RSA-ARIA128-GCM-SHA256, ADH-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES256-SHA384, DHE-RSA-AES256-SHA256, DHE-DSS-AES256-SHA256, ECDHE-ECDSA-CAMELLIA256-SHA384, ECDHE-RSA-CAMELLIA256-SHA384, DHE-RSA-CAMELLIA256-SHA256, DHE-DSS-CAMELLIA25  
                                         6-SHA256, ADH-AES256-SHA256, ADH-CAMELLIA256-SHA256, ECDHE-ECDSA-AES128-SHA256, ECDHE-RSA-AES128-SHA256, DHE-RSA-AES128-SHA256, DHE-DSS-AES128-SHA256, ECDHE-ECDSA-CAMELLIA128-SHA256, ECDHE-RSA-CAMELLIA128-SHA256, DHE-RSA-CAMELLIA128-SHA256, DHE-DSS-CAMELLIA128-SHA256, ADH  
                                         -AES128-SHA256, ADH-CAMELLIA128-SHA256, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES256-SHA, DHE-RSA-AES256-SHA, DHE-DSS-AES256-SHA, DHE-RSA-CAMELLIA256-SHA, DHE-DSS-CAMELLIA256-SHA, AECDH-AES256-SHA, ADH-AES256-SHA, ADH-CAMELLIA256-SHA, ECDHE-ECDSA-AES128-SHA, ECDHE-RSA-AES128-  
                                         SHA, DHE-RSA-AES128-SHA, DHE-DSS-AES128-SHA, DHE-RSA-SEED-SHA, DHE-DSS-SEED-SHA, DHE-RSA-CAMELLIA128-SHA, DHE-DSS-CAMELLIA128-SHA, AECDH-AES128-SHA, ADH-AES128-SHA, ADH-SEED-SHA, ADH-CAMELLIA128-SHA, RSA-PSK-AES256-GCM-SHA384, DHE-PSK-AES256-GCM-SHA384, RSA-PSK-CHACHA20-P  
                                         OLY1305, DHE-PSK-CHACHA20-POLY1305, ECDHE-PSK-CHACHA20-POLY1305, DHE-PSK-AES256-CCM8, DHE-PSK-AES256-CCM, RSA-PSK-ARIA256-GCM-SHA384, DHE-PSK-ARIA256-GCM-SHA384, AES256-GCM-SHA384, AES256-CCM8, AES256-CCM, ARIA256-GCM-SHA384, PSK-AES256-GCM-SHA384, PSK-CHACHA20-POLY1305,  
                                         PSK-AES256-CCM8, PSK-AES256-CCM, PSK-ARIA256-GCM-SHA384, RSA-PSK-AES128-GCM-SHA256, DHE-PSK-AES128-GCM-SHA256, DHE-PSK-AES128-CCM8, DHE-PSK-AES128-CCM, RSA-PSK-ARIA128-GCM-SHA256, DHE-PSK-ARIA128-GCM-SHA256, AES128-GCM-SHA256, AES128-CCM8, AES128-CCM, ARIA128-GCM-SHA256,  
                                         PSK-AES128-GCM-SHA256, PSK-AES128-CCM8, PSK-AES128-CCM, PSK-ARIA128-GCM-SHA256, AES256-SHA256, CAMELLIA256-SHA256, AES128-SHA256, CAMELLIA128-SHA256, ECDHE-PSK-AES256-CBC-SHA384, ECDHE-PSK-AES256-CBC-SHA, SRP-DSS-AES-256-CBC-SHA, SRP-RSA-AES-256-CBC-SHA, SRP-AES-256-CBC-S  
                                         HA, RSA-PSK-AES256-CBC-SHA384, DHE-PSK-AES256-CBC-SHA384, RSA-PSK-AES256-CBC-SHA, DHE-PSK-AES256-CBC-SHA, ECDHE-PSK-CAMELLIA256-SHA384, RSA-PSK-CAMELLIA256-SHA384, DHE-PSK-CAMELLIA256-SHA384, AES256-SHA, CAMELLIA256-SHA, PSK-AES256-CBC-SHA384, PSK-AES256-CBC-SHA, PSK-CAME  
                                         LLIA256-SHA384, ECDHE-PSK-AES128-CBC-SHA256, ECDHE-PSK-AES128-CBC-SHA, SRP-DSS-AES-128-CBC-SHA, SRP-RSA-AES-128-CBC-SHA, SRP-AES-128-CBC-SHA, RSA-PSK-AES128-CBC-SHA256, DHE-PSK-AES128-CBC-SHA256, RSA-PSK-AES128-CBC-SHA, DHE-PSK-AES128-CBC-SHA, ECDHE-PSK-CAMELLIA128-SHA256  
                                         , RSA-PSK-CAMELLIA128-SHA256, DHE-PSK-CAMELLIA128-SHA256, AES128-SHA, SEED-SHA, CAMELLIA128-SHA, IDEA-CBC-SHA, PSK-AES128-CBC-SHA256, PSK-AES128-CBC-SHA, PSK-CAMELLIA128-SHA256)  
  SSLVersion  All              yes       SSL version to test (Accepted: All, SSLv3, TLSv1.0, TLSv1.2, TLSv1.3)  
  THREADS     1                yes       The number of concurrent threads (max one per host)  
  
  
View the full module info with the info, or info -d command.

msf auxiliary(scanner/ssl/ssl_version) > set threads 8

msf auxiliary(scanner/ssl/ssl_version) > set rhosts <target_IP>

msf auxiliary(scanner/ssl/ssl_version) > run
```
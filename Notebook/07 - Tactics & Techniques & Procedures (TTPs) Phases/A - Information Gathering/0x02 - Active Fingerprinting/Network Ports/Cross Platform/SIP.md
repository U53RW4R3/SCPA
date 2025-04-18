---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-protocols
  - sip
  - metasploit-framework
---
# SIP

## 01 - Manual

TODO: write more about manual SIP enumeration

```
$ svmap <IP>/<CIDR> -v

$ svmap <start_IP>-<end_IP> -v
```

```
$ sipvicious
```

## 02 - Metasploit

```
msf > use auxiliary/scanner/sip/enumerator

msf auxiliary(scanner/sip/enumerator) > options

Module options (auxiliary/scanner/sip/enumerator):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to probe in each set
   CHOST                       no        The local client address
   CPORT      5060             no        The local client port
   MAXEXT     9999             yes       Ending extension
   METHOD     REGISTER         yes       Enumeration method (Accepted: OPTIONS, REGISTER)
   MINEXT     0                yes       Starting extension
   PADLEN     4                yes       Cero padding maximum length
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      5060             yes       The target port
   THREADS    1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/sip/enumerator) > set rhosts <IP>/<CIDR>

msf auxiliary(scanner/sip/enumerator) > run
```

```
auxiliary/scanner/sip/enumerator_tcp
```

```
auxiliary/scanner/sip/sipdroid_ext_enum
```

---
## References

- [Sipvicious](https://github.com/EnableSecurity/sipvicious)

- [SVMap Usage](https://github.com/EnableSecurity/sipvicious/wiki/SVMap-Usage)

- [Enable Security: An overview of the VoIP and RTC offensive security toolset, SIPVicious PRO](https://www.youtube.com/watch?v=9EL8Swns9z0)
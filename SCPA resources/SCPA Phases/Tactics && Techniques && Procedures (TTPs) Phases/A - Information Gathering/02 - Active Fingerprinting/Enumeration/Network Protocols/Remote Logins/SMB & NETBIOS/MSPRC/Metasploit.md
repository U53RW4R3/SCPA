# Metasploit

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

- Metasploit auxiliary module Endpoint Mapper Service Discovery

```
msf > use auxiliary/scanner/dcerpc/endpoint_mapper

msf auxiliary(scanner/dcerpc/endpoint_mapper) > options

Module options (auxiliary/scanner/dcerpc/endpoint_mapper):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    135              yes       The target port (TCP)
   THREADS  1                yes       The number of concurrent threads (max one per host)


View the full module info with the info, or info -d command.

msf auxiliary(scanner/dcerpc/endpoint_mapper) > set threads 8

msf auxiliary(scanner/dcerpc/endpoint_mapper) > set rhosts <IP>

msf auxiliary(scanner/dcerpc/endpoint_mapper) > run
```

- Metasploit auxiliary module Hidden DCERPC Service Discovery

```
msf > use auxiliary/scanner/dcerpc/hidden

msf auxiliary(scanner/dcerpc/hidden) > options

Module options (auxiliary/scanner/dcerpc/hidden):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   THREADS  1                yes       The number of concurrent threads (max one per host)


View the full module info with the info, or info -d command.

msf auxiliary(scanner/dcerpc/hidden) > set threads 2

msf auxiliary(scanner/dcerpc/hidden) > set rhosts <IP>

msf auxiliary(scanner/dcerpc/hidden) > run
```

- Metasploit auxiliary module Remote Management Interface Discovery

```
msf > use auxiliary/scanner/dcerpc/management

msf auxiliary(scanner/dcerpc/management) > options

Module options (auxiliary/scanner/dcerpc/management):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    135              yes       The target port (TCP)
   THREADS  1                yes       The number of concurrent threads (max one per host)


View the full module info with the info, or info -d command.

msf auxiliary(scanner/dcerpc/management) > set threads 2

msf auxiliary(scanner/dcerpc/management) > set rhosts <IP>

msf auxiliary(scanner/dcerpc/management) > run
```

- Metasploit auxiliary module Remote Management Interface Discovery

```
msf > use auxiliary/scanner/dcerpc/tcp_dcerpc_auditor

msf auxiliary(scanner/dcerpc/tcp_dcerpc_auditor) > options

Module options (auxiliary/scanner/dcerpc/tcp_dcerpc_auditor):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    135              yes       The target port (TCP)
   THREADS  1                yes       The number of concurrent threads (max one per host)


View the full module info with the info, or info -d command.

msf auxiliary(scanner/dcerpc/tcp_dcerpc_auditor) > set threads 2

msf auxiliary(scanner/dcerpc/tcp_dcerpc_auditor) > set rhosts <IP>

msf auxiliary(scanner/dcerpc/tcp_dcerpc_auditor) > run
```
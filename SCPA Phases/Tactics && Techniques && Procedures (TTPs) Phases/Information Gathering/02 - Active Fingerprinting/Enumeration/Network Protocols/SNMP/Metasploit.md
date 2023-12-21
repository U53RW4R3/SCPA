# Metasploit

## 01 - SNMP Enumeration

```
msf > use auxiliary/scanner/snmp/snmp_enum

msf auxiliary(scanner/snmp/snmp_enum) > options

Module options (auxiliary/scanner/snmp/snmp_enum):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   COMMUNITY  public           yes       SNMP Community String
   RETRIES    1                yes       SNMP Retries
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      161              yes       The target port (UDP)
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    1                yes       SNMP Timeout
   VERSION    1                yes       SNMP Version <1/2c>

msf auxiliary(scanner/snmp/snmp_enum) > set community <public | private>

msf auxiliary(scanner/snmp/snmp_enum) > set version <1 | 2c>

msf auxiliary(scanner/snmp/snmp_enum) > set rhosts <IP>

msf auxiliary(scanner/snmp/snmp_enum) > run
```

## 02 - Shares

```
msf > use auxiliary/scanner/snmp/snmp_enumshares

msf auxiliary(scanner/snmp/snmp_enumshares) > options

Module options (auxiliary/scanner/snmp/snmp_enumshares):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   COMMUNITY  public           yes       SNMP Community String
   RETRIES    1                yes       SNMP Retries
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      161              yes       The target port (UDP)
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    1                yes       SNMP Timeout
   VERSION    1                yes       SNMP Version <1/2c>

msf auxiliary(scanner/snmp/snmp_enumshares) > set community <public | private>

msf auxiliary(scanner/snmp/snmp_enumshares) > set version <1 | 2c>

msf auxiliary(scanner/snmp/snmp_enumshares) > set rhosts <IP>

msf auxiliary(scanner/snmp/snmp_enumshares) > run
```

## 03 - Enumerate Users

```
msf > use auxiliary/scanner/snmp/snmp_enumusers

msf auxiliary(scanner/snmp/snmp_enumusers) > options

Module options (auxiliary/scanner/snmp/snmp_enumusers):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   COMMUNITY  public           yes       SNMP Community String
   RETRIES    1                yes       SNMP Retries
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      161              yes       The target port (UDP)
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    1                yes       SNMP Timeout
   VERSION    1                yes       SNMP Version <1/2c>

msf auxiliary(scanner/snmp/snmp_enumusers) > set community <public | private>

msf auxiliary(scanner/snmp/snmp_enumusers) > set version <1 | 2c>

msf auxiliary(scanner/snmp/snmp_enumusers) > run
```

## 04 - SNMP Set OID

```
msf > use auxiliary/scanner/snmp/snmp_set

msf auxiliary(scanner/snmp/snmp_set) > options

Module options (auxiliary/scanner/snmp/snmp_set):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   COMMUNITY  public           yes       SNMP Community String
   OID                         yes       The object identifier (numeric notation)
   OIDVALUE                    yes       The value to set
   RETRIES    1                yes       SNMP Retries
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      161              yes       The target port (UDP)
   THREADS    1                yes       The number of concurrent threads (max one per host)
   TIMEOUT    1                yes       SNMP Timeout
   VERSION    1                yes       SNMP Version <1/2c>

msf auxiliary(scanner/snmp/snmp_set) > set community <public | private>

msf auxiliary(scanner/snmp/snmp_set) > set version <1 | 2c>

msf auxiliary(scanner/snmp/snmp_set) > set oid <oid>

msf auxiliary(scanner/snmp/snmp_set) > set oidvalue <oid_value>

msf auxiliary(scanner/snmp/snmp_set) > set rhosts <IP>
```
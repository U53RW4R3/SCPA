# SNMP

## 01 - Manual

### 1.1 - `snmp-check`

```
$ snmp-check <IP>

$ snmp-check -v2c -c public <IP>

$ snmp-check -p <PORT> <IP>
```

### 1.2 - `snmpwalk`

Syntax usage.

```
$ snmpwalk -c public -v1 <IP>

$ snmpwalk -v 2c -c public <IP>:<PORT>
```

### 1.3 - Samrdump

```
$ samrdump SNMP <IP>
```

## 02 - Nmap

```
$ nmap -p 161,162 -sU --script snmp-enum <IP>
```

## 03 - Metasploit

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

msf auxiliary(scanner/snmp/snmp_enum) > set community <password>

msf auxiliary(scanner/snmp/snmp_enum) > set version <1 | 2c>

msf auxiliary(scanner/snmp/snmp_enum) > set rhosts <target_IP>

msf auxiliary(scanner/snmp/snmp_enum) > set rport <target_PORT>

msf auxiliary(scanner/snmp/snmp_enum) > run
```

---
## References

- [Hacktricks: Pentesting SNMP](https://book.hacktricks.xyz/pentesting/pentesting-snmp)

- [RangeForce: Enumerating with Nmap](https://materials.rangeforce.com/tutorial/2020/01/30/Enumerating-with-Nmap/)
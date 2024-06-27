# Manual

## 01 - Snmp-check

`$ snmp-check <IP>`

`$ snmp-check -v2c -c public <IP>`

`$ snmp-check -p <PORT> <IP>`

## 02 - Snmpwalk

### 2.1 - Usage

`$ snmpwalk -c public -v1 <IP>`

`$ snmpwalk -v 2c -c public <IP>:<PORT>`

### 2.2 - Enumerate Windows Users

```
$ snmpwalk -c public -v1 <IP> | grep | cut -d " " -f 4

$ snmpwalk -v 2c -c public <IP>:<PORT> | grep | cut -d " " -f 4
```

### 2.3 - Enumerate Running Services

```
$ snmpwalk -c public -v1 <IP> | grep hrSWRunName | cut -d " " -f 4

$ snmpwalk -v 2c -c public <IP>:<PORT> | grep hrSWRunName | cut -d " " -f 4
```

### 2.4 - Enumerate Open TCP Ports

```
$ snmpwalk -c public -v1 <IP> | grep tcpConnState | cut -d "." -f 6 | sort -nu

$ snmpwalk -v 2c -c public <IP>:<PORT> | grep tcpConnState | cut -d "." -f 6 | sort -nu
```

### 2.5 - Enumerate Installed Programs

```
$ snmpwalk -c public -v1 <IP> | grep hrSWInstalledName | cut -d " " -f 4

$ snmpwalk -v 2c -c public <IP>:<PORT> | grep hrSWInstalledName | cut -d " " -f 4
```

## 03 - Samrdump

```
$ samrdump SNMP <IP>
```

## 04 - Onesixtyone

```
$ onesixtyone -w 0 <IP>

$ onesixtyone -c <private | public> -i snmp_ip_targets.txt
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/A - Information Gathering/02 - Active Fingerprinting/Enumeration/Network Protocols/Remote Logins/Telnet/Telnet|Active Enumeration: Telnet]]

- [Pentesting SNMP](https://book.hacktricks.xyz/pentesting/pentesting-snmp)
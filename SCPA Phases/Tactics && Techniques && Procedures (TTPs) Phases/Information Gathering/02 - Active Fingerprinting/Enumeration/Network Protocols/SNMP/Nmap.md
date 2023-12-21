# Nmap

## 01 - Interfaces

`$ nmap -p 161 -sU --script snmp-interfaces --script-args creds.snmp=<password> <IP>`

## 02 - Netstat

`$ nmap -p 161 -sU --script snmp-netstat --script-args creds.snmp=<password> <IP>`

## 03 - Processes

`$ nmap -p 161 -sU --script snmp-processes --script-args creds.snmp=<password> <IP>`

## 04 - SNMP Enumeration

`$ nmap -p 161 -sU --script snmp-enum <IP>`

---
## References

- [RangeForce: Enumerating with Nmap](https://materials.rangeforce.com/tutorial/2020/01/30/Enumerating-with-Nmap/)
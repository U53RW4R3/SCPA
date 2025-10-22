---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-protocols
  - sap
  - network-mapper
  - metasploit-framework
---
# SAP

## 01 - Common Ports

```
$ nmap -p 3200-3299,3300-3399,8000-8099,8100-8199 -Pn -sV <IP>
```

## 02 - Banner Grab

```
msf > auxiliary/scanner/sap/sap_mgmt_con_version

msf auxiliary(scanner/sap/sap_mgmt_con_version) > run rhosts=<IP> rport=<PORT>
```

## 03 - Service Discovery

```
msf > use auxiliary/scanner/sap/sap_service_discovery

msf auxiliary(scanner/sap/sap_service_discovery) > run rhosts=<IP> rport=<PORT>
```

## 04 - Information Request

```
msf > use auxiliary/scanner/sap/sap_router_info_request

msf auxiliary(scanner/sap/sap_router_info_request) > run rhosts=<IP> rport=<PORT>
```

## 05 - Port Scanner

> [!INFO]
> If the scanner was able to discover `SAP Router` open port. This can be used as a proxy to enumerate deeper in the network port.

```
msf > use auxiliary/scanner/sap/sap_router_portscanner

msf auxiliary(scanner/sap/sap_router_portscanner) > set ports 32NN,80NN

msf auxiliary(scanner/sap/sap_router_portscanner) > run rhosts=<IP> rport=<PORT>
```

## 06 - System Information

```
msf > use auxiliary/scanner/sap/sap_soap_rfc_system_info

msf auxiliary(scanner/sap/sap_soap_rfc_system_info) > set httpusername <username>

msf auxiliary(scanner/sap/sap_soap_rfc_system_info) > set httppassword <password>

msf auxiliary(scanner/sap/sap_soap_rfc_system_info) > run rhosts=<IP> rport=<PORT>
```

## 07 - RFC Table

```
msf > use auxiliary/scanner/sap/sap_soap_rfc_read_table

msf auxiliary(scanner/sap/sap_soap_rfc_read_table) > set table <table_name>

msf auxiliary(scanner/sap/sap_soap_rfc_read_table) > set fields BNAME,BCODE,GLTGV,GLTGB,USTYP,CLASS,LOCNT,ACCNT,ANAME,ERDAT,TRDAT,LTIME,OCOD1,BCDA1,CODV1,OCOD2,BCCDA2,CODV2,OCOD3,BCDA3,CODV3,OCOD4,BCDA2,CODV2,OCOD3,VERSN,TZONE,PASSCODE,PWDHISTORY

msf auxiliary(scanner/sap/sap_soap_rfc_read_table) > set httpusername <username>

msf auxiliary(scanner/sap/sap_soap_rfc_read_table) > set httppassword <password>

msf auxiliary(scanner/sap/sap_soap_rfc_read_table) > run rhosts=<IP> rport=<PORT>
```

## 08 - Path Traversal

```
msf > use auxiliary/scanner/sap/sap_soap_rfc_eps_get_directory_listing

msf auxiliary(scanner/sap/sap_soap_rfc_eps_get_directory_listing) > set httpusername <username>

msf auxiliary(scanner/sap/sap_soap_rfc_eps_get_directory_listing) > set httppassword <password>

msf auxiliary(scanner/sap/sap_soap_rfc_eps_get_directory_listing) > run rhosts=<IP> rport=<PORT>
```

## 09 - OS File Existence

```
msf > use auxiliary/scanner/sap/sap_soap_rfc_pfl_check_os_file_existence

msf auxiliary(scanner/sap/sap_soap_rfc_pfl_check_os_file_existence) > set httpusername <username>

msf auxiliary(scanner/sap/sap_soap_rfc_pfl_check_os_file_existence) > set httppassword <password>

msf auxiliary(scanner/sap/sap_soap_rfc_pfl_check_os_file_existence) > run rhosts=<IP> rport=<PORT>
```

## 10 - Log Files

```
msf > use auxiliary/scanner/sap/sap_mgmt_con_getlogfiles
```

## 11 - Get Environment

```
msf > use auxiliary/scanner/sap/sap_mgmt_con_getenv
```

## 12 - Extract Users

```
msf > use auxiliary/scanner/sap/sap_mgmt_con_extractusers
```

## 13 - Access Points

```
msf > use auxiliary/scanner/sap/sap_mgmt_con_getaccesspoints
```

## 14 - Process List

```
msf > use auxiliary/scanner/sap/sap_mgmt_con_getprocesslist
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xD - Network Ports/SAP]]

### Hacktricks

- [Hacktricks: Pentesting SAP](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-sap.html)

### Walter Oberacher

- [Walter Oberacher: SAP PENTEST](https://medium.com/swlh/erp-pentest-metasploit-writeup-e65de8ece7d1)

### Red & Blue Team Security

- [Red & Blue Team Security: Penetration Testing SAP Systems - A Real-World Case Study I](https://www.rbtsec.com/blog/unlocking-the-secrets-of-sap-penetration-testing/)
---
author(s):
  - Userware
tags:
  - information-gathering
  - passive-fingerprinting
  - networking
  - network-protocols
  - dns
---
# References DNS Records

## Commonly used record types

| Field | Description                                  | Value                            |
| ----- | -------------------------------------------- | -------------------------------- |
| A     | IPv4 Host Address                            | 32-bit integer                   |
| AAAA  | IPv6 host address                            | 64-bit hexadecimal               |
| ALIAS | Auto resolved alias                          |                                  |
| CNAME | Canonical name for an alias                  |                                  |
| MX    | Mail eXchange                                | The domain that will accept mail |
| NS    | Name Server                                  |                                  |
| PTR   | Pointer                                      |                                  |
| SOA   | Start Of Authority                           |                                  |
| SRV   | location of service                          |                                  |
| TXT   | Descriptive text                             |                                  |
| ANY   | Specifies all types of data                  |                                  |
| GID   | Specifies a group identifier of a group name |                                  |
| UID   | Specifies the user identifier                |                                  |

## Records types used for DNSSEC

| Field      | Description                   | Value |
| ---------- | ----------------------------- | ----- |
| DNSKEY     | DNSSEC public key             |       |
| DS         | Delegation Signer             |       |
| NSEC       | Next Secure                   |       |
| NSEC3      | Next Secure v. 3              |       |
| NSEC3PARAM | NSEC3 Parameters              |       |
| RRSIG      | RRset Signature               |       |

## Less commonly used record types

| Field | Description                             | Value |
| ----- | --------------------------------------- | ----- |
| AFSDB | AFS Data Base location                  |       |
| ATMA  | Asynchronous Transfer Mode Address      |       |
| CAA   | Certification Authority Authorization   |       |
| CERT  | Certificate / CRL                       |       |
| DHCID | DHCP Information                        |       |
| DNAME | Non-Terminal DNS Name Redirection       |       |
| HINFO | Host information                        |       |
| ISDN  | ISDN address                            |       |
| LOC   | LOCation information                    |       |
| MB    | mailbox records                         |       |
| MG    | mailbox records                         |       |
| MINFO | mailbox records                         |       |
| MR    | mailbox records                         |       |
| NAPTR | Naming Authority Pointer                |       |
| NSAP  | NSAP address                            |       |
| RP    | Responsible Person                      |       |
| RT    | Route Through                           |       |
| TLSA  | Transport Layer Security Authentication |       |
| X25   | X.25 PSDN address                       |       |
| UINFO | Specifies the user information          |       |
| WKS   | Describes a Well-Known Service          |       |

## Zytrax

- [Zytrax: DNSBL (DNS Black List)](https://www.zytrax.com/books/dns/ch9/dnsbl.html)
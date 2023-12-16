# Manual

## 01 - Usage

- Scanning for NetBIOS hosts

`$ nmblookup -A <IP>`

`$ nbtscan <IP>/<CIDR>`

`$ nbtscan –v –s : <IP>/<CIDR> | cut -d ":" –f 1 > smb-hosts.txt`

- Authenticating with NetBIOS protocol

`$ rpcclient -U <username>%<password> <IP>`

## 02 - Enumeration

### 2.1 - Anonymous Login

TODO: Duplicate this in the post exploitation section

- Check for anonymous login

`$ rpcclient -U "" -N <IP>`


TODO: Re-arrange them in post exploitation section

### 2.2 - Basic Information

- Retrieve user domain password information

`rpcclient $> getusrdompwinfo <RID>`

### 2.3 - Domain Users

- Enumerate Domain Users

`rpcclient $> enumdomusers`

`rpcclient $> enumalsgroups builtin`

`rpcclient $> queryuser <username>`

`rpcclient $> queryusersgroups <rid>`

- Display Query Information

`rpcclient $> querydispinfo`

- Enumerate Privileges

`rpcclient $> enumprivs`

### 2.4 - LSA Query

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

### 2.5 - Domain Groups

- Enumerate Domain Groups

`rpcclient $> enumdomgroups`

`rpcclient $> querygroup <rid>`

`rpcclient $> querygroupmem <rid>`

- Domain Information

`rpcclient $> querydominfo`

`rpcclient $> enumdomains`

- Domain Password Information

`rpcclient $> getdompwinfo`

- Retrieve information of SMB shares

`rpcclient $> netshareenum`

`rpcclient $> netshareenumall`

`rpcclient $> netsharegetinto <share_name>`

## 03 - Create Accounts

- Create domain user account

`rpcclient $> createdomuser <username>`

`rpcclient $> setuserinfo2 <username> 24 <password>`

`rpcclient $> enumdomusers`

- LSA create account

`rpcclient $> lsaenumsid`

`rpcclient $> lookupsids S-1-1-0`

Lookup username accounts

`rpcclient $> lookupnames <username>`

`rpcclient $> lsacreateaccount S-1-1-0`

`rpcclient $> lsaaddpriv S-1-1-0 SeCreateTokenPrivilege`

`rpcclient $> lsaenumprivsaccount S-1-1-0`

## 04 - Change Passwod Accounts

`rpcclient $> chgpasswd <username> <old_password> <new_password>`

## 05 - Delete Accounts

- Delete user account

`rpcclient $> deletedomuser <username>`

- Delete domain group

`rpcclient $> deletedomgroup <group_name>`

`rpcclient $> enumdomgroups`

- Delete LSA account privileges

`rpcclient $> lsadelpriv S-1-1-0`

`rpcclient $> lsaenumprivsaccount S-1-1-0`
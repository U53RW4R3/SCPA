# NFS

## 01 - Banner Grab

```
$ nmap -p 111,2049 -sV <IP>
```

## 01 - Manual

### 1.1 - Display Mount Drives

```
$ sudo apt install -y nfs-common
```

```
$ rpcinfo <IP>

$ showmount -e <IP>
```

### 1.2 - Mount Drives

```
$ sudo mkdir /mnt/nfs

$ sudo mount -t nfs -o rw <IP>:</directory> /mnt/nfs
```

Mount older Linux or Unix-like systems

```
$ sudo mount -t nfs -o rw,vers=2 <IP>:</directory> /mnt/nfs

$ sudo mount -t nfs -o nolock <IP>:</directory> /mnt/nfs
```

Unmount the shared folder once the infiltration has been and clean up the logs

```
$ sudo umount /mnt/nfs
```

## 02 - Network Mapper

```
$ nmap -p 111,2049 -sV --script nfs-ls,nfs-showmount,nfs-statfs,rpcinfo <IP>

$ nmap -p 111,2049 -sV --script nfs-*,rpcinfo <IP>
```

## 03 - Metasploit

```
msf > use auxiliary/scanner/nfs/nfsmount

msf auxiliary(scanner/nfs/nfsmount) > options

Module options (auxiliary/scanner/nfs/nfsmount):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   PROTOCOL  udp              yes       The protocol to use (Accepted: udp, tcp)
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     111              yes       The target port (TCP)
   THREADS   1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/nfs/nfsmount) > set protocol <udp | tcp>

msf auxiliary(scanner/nfs/nfsmount) > set rhosts <IP>

msf auxiliary(scanner/nfs/nfsmount) > set rport <PORT>

msf auxiliary(scanner/nfs/nfsmount) > set threads 2

msf auxiliary(scanner/nfs/nfsmount) > run
```

---
## References

### Hacktricks

- [Hacktricks: Pentesting Portmapper](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-rpcbind.html)

- [Hacktricks: Pentesting NFS Service](https://book.hacktricks.wiki/en/network-services-pentesting/nfs-service-pentesting.html)
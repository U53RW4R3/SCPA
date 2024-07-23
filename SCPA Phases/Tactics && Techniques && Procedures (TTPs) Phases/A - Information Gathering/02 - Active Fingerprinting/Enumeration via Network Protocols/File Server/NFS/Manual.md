# Manual

## 01 - Usage

### 1.1 - Display Mount Drives

`$ showmount -e <IP>`

`$ rpcinfo <IP>`

### 1.2 - Mount Drives

`$ sudo mkdir /mnt/nfs`

`$ sudo mount -t nfs -o rw <IP>:</directory> /mnt/nfs`

- Mount older Linux or Unix-like systems

`$ sudo mount -t nfs -o rw,vers=2 <IP>:</directory> /mnt/nfs`

- Unmount the shared folder once the infiltration has been and clean up the logs

`$ sudo umount /mnt/nfs`

---
## References

- [Hacktricks: Pentesting Portmapper](https://book.hacktricks.xyz/network-services-pentesting/pentesting-rpcbind)
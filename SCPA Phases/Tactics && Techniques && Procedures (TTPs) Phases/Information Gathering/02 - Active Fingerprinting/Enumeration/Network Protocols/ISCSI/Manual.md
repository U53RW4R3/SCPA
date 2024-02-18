# Manual

## 01 - Install Dependencies

`$ sudo apt-get install open-iscsi`

## 02 - Discovery Targets

`$ iscsiadm -m discovery -t sendtargets -p <IP>:3260`

## 03 - Mount the node

- Login the node

`$ iscsiadm -m node --targetname="<target_node>" -p <IP>:3260 -l`

- Initiator

`$ cat /etc/iscsi/initiatorname.iscsi`

- List the mounted drives

```
$ ls /dev/sd*

$ sudo fdisk -l
```

- Mount the node

`$ sudo mount /dev/sdX[n] /mnt`

## 04 - Logout Node

- unmount the node

`$ sudo umount /mnt`

- Logout the node

`$ iscsiadm -m node --targetname="<target_node>" -p <IP>:3260 -u`

---
## References

- [Hacktricks: 3260 Pentesting ISCSI](https://book.hacktricks.xyz/network-services-pentesting/3260-pentesting-iscsi)
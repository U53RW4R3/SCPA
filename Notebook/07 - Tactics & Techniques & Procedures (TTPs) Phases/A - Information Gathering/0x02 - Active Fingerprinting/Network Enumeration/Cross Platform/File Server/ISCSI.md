# ISCSI

## 01 - Install Dependencies

```
$ sudo apt-get install open-iscsi
```

## 02 - Discovery Targets

### 2.1 - Network Mapper

```
$ nmap -p 3260 -Pn -n -sV --script iscsi-info <IP>
```

### 2.2 - Manual

```
$ iscsiadm -m discovery -t sendtargets -p <IP>:3260
```

## 03 - Mount the node

Login the node

```
$ iscsiadm -m node --targetname="<target_node>" -p <IP>:3260 -l
```

Initiator

```
$ cat /etc/iscsi/initiatorname.iscsi
```

List the mounted drives

```
$ ls /dev/sd*

$ sudo fdisk -l
```

Mount the node

```
$ sudo mount /dev/sdX[n] /mnt
```

## 04 - Logout Node

Unmount the node

```
$ sudo umount /mnt
```

Logout the node

```
$ iscsiadm -m node --targetname="<target_node>" -p <IP>:3260 -u
```

---
## References

### Hacktricks

- [Hacktricks: 3260 Pentesting ISCSI](https://book.hacktricks.wiki/en/network-services-pentesting/3260-pentesting-iscsi.html)
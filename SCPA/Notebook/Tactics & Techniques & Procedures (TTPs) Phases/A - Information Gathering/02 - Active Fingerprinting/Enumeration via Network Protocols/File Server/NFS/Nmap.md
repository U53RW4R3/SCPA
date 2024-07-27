# Nmap

`$ nmap -p 111,2049 -sV --script nfs-ls,nfs-showmount,nfs-statfs,rpc-info <IP>`

`$ nmap -p 111,2049 -sV --script nfs-*,rpcinfo <IP>`

---
## References

- [RangeForce: Enumerating with Nmap](https://materials.rangeforce.com/tutorial/2020/01/30/Enumerating-with-Nmap/)
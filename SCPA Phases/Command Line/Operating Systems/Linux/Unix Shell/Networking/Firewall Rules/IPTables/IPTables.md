# IPTables

## 01 - Create Rules

- **SSH inbound rule connection**

`$ sudo iptables -A INPUT -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT`

## 02 - Modify Rules

`$ sudo iptables`

## 03 - Delete Rules

`$ sudo iptables`

---
## References

- [Hackers Arise: Linux Basics for Hackers, Part 11: Linux Firewalls (iptables)](https://www.hackers-arise.com/post/linux-basics-for-hackers-part-11-linux-firewalls-iptables)
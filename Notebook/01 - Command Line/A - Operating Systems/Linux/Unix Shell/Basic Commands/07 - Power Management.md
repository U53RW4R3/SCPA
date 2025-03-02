---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 07 - Power Management

## 7.1 - Shutdown Computer

Turn off the computer in an instant.

```
$ shutdown -P now

$ poweroff

$ systemctl poweroff -i
```

## 7.2 - Restart Computer

```
$ reboot

$ systemctl -i reboot
```

## 7.3 - Suspend Computer

```
$ systemctl suspend
```

## 7.4 - Hibernate Mode

```
$ systemctl hibernate
```
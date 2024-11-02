---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 08 - Power Management

## 8.1 - Shutdown Computer

Turn off the computer in an instant.

```
$ shutdown -P now

$ poweroff

$ systemctl poweroff -i
```

## 8.2 - Restart Computer

```
$ reboot

$ systemctl -i reboot
```

## 8.3 - Suspend Computer

```
$ systemctl suspend
```

## 8.4 - Hibernate Mode

```
$ systemctl hibernate
```
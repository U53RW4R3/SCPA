---
author(s):
  - Userware
tags:
  - operation-security
  - spoofing
  - command-line
  - linux
---
# Change Hostname

^6caa22

Change the computer name of your machine.

```
$ hostnamectl hostname "<windows_workstation_name_to_spoof>"

$ sudo nmtui-hostname
```

^09eb5b

Or you can append it in a line.

```
# echo "<windows_workstation_name_to_spoof>" > /etc/hostname

# hostname -F /etc/hostname
```

Once you're changed the `hostname`. Restart the terminal to apply it.

```
$ reset
```

^153cb6

---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - adb
  - network-mapper
  - android
---
# ADB (Android Debug Bridge)

## 01 - Banner Grab

```
$ nmap -p 5555 -Pn -sV <IP>
```

## 02 - Connect

```
$ adb connect <IP>[:<PORT>]
```

List connected devices.

```
$ adb devices -l
```

---
## References

### Hacktricks

- [Hacktricks: Android Debug Bridge](https://book.hacktricks.wiki/en/network-services-pentesting/5555-android-debug-bridge.html)

- [Hacktricks: ADB Commands](https://book.hacktricks.wiki/en/mobile-pentesting/android-app-pentesting/adb-commands.html)

### Hacking Articles

- [Hacking Articles: Android Pentest Lab Setup & ADB Command Cheatsheet](https://www.hackingarticles.in/android-pentest-lab-setup-adb-command-cheatsheet/)
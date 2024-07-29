# ADB (Android Debug Bridge)

## Nmap

```
$ nmap -p 5555 -Pn -sV <IP>
```

## Connect

```
$ adb connect <IP>[:<PORT>]
```

List connected devices.

```
$ adb devices -l
```

---
## References

- [Hacktricks: Android Debug Bridge](https://book.hacktricks.xyz/network-services-pentesting/5555-android-debug-bridge)

- [Hacktricks: ADB Commands](https://book.hacktricks.xyz/mobile-pentesting/android-app-pentesting/adb-commands)

- [Hacking Articles: Android Pentest Lab Setup & ADB Command Cheatsheet](https://www.hackingarticles.in/android-pentest-lab-setup-adb-command-cheatsheet/)
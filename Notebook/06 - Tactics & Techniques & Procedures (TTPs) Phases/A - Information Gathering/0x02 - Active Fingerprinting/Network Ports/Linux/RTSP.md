---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - rtsp
  - network-mapper
---
# RTSP

## 01 - Banner Grab

```
$ nmap -p 554 -Pn -sV <IP>
```

## 02 - RTSP methods

```
$ nmap -p 554 -Pn --script rtsp-methods <IP>
```

## 03 - Brute Force URL

```
$ nmap -p 554 -Pn --script rtsp-url-brute <IP>
```

## 04 - Authenticate 

### 4.1 - Install FFmpeg

Install the package according to your package manager.

```
$ sudo apt install -y ffmpeg

$ sudo pacman -S ffmpeg
```

### 4.2 - Install MPV

Install the package according to your package manager.

```
$ sudo apt install -y mpv

$ sudo pacman -S mpv
```

The usage syntax as it follows.

```
$ ffplay rtsp://[<username>:<password>@]<IP>[:<PORT>]

$ mpv rtsp://[<username>:<password>@]<IP>[:<PORT>]
```

---
## References

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/0x03 - Network Ports/IoTs/CCTV/RTSP|Vulnerability Assessment: RTSP]]
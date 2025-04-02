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

## 01 - RTSP methods

```
$ nmap -p 554 -Pn --script rtsp-methods <IP>
```

## 02 - Whole Enumeration

```
$ nmap -p 554 -Pn --script rtsp-methods,rtsp-url-brute <IP>
```

## 03 - Authenticate 

### 3.1 - Install FFmpeg

Install the package according to your package manager.

```
$ sudo apt install -y ffmpeg

$ sudo pacman -S ffmpeg
```

### 3.2 - Install MPV

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

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/03 - Network Ports/RTSP|Vulnerability Assessment: RTSP]]
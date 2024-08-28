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

```
$ sudo apt install -y ffmpeg
```

### 3.2 - Install MPV

```
$ sudo apt install -y mpv
```

The usage syntax as it follows.

```
$ ffplay rtsp://[<username>:<password>@]<IP>[:<PORT>]

$ mpv rtsp://[<username>:<password>@]<IP>[:<PORT>]
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/04 - Vulnerable Network Protocols/RTSP|Vulnerability Assessment: RTSP]]
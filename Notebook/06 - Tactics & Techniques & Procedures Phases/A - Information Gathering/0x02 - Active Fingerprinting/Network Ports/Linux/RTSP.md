---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - rtsp
---
# RTSP

## 01 - Banner Grab

```
$ nmap -p 554 -Pn -sV <IP>
```

## 02 - Enumerate RTSP Methods

### 2.1 - Manual

```
$ curl -i -X OPTIONS rtsp://<IP>[:<PORT>]/stream RTSP/1.1
```

### 2.2 - #network-mapper 

```
$ nmap -p 554 -Pn --script rtsp-methods <IP>
```

## 03 - Brute Force URL

```
$ nmap -p 554 -Pn --script rtsp-url-brute <IP>
```

## 04 - Authenticate

### 4.1 - Video Stream

```
$ ffplay rtsp://[<username>:<password>@]<IP>[:<PORT>]

$ ffmpeg -rtsp_transport tcp -i rtsp://[<username>:<password>@]<IP>[:<PORT>]/stream -c copy output.mp4

$ mpv rtsp://[<username>:<password>@]<IP>[:<PORT>]
```

### 4.2 - Capture Screenshot

```
$ ffmpeg -rtsp_transport tcp -i rtsp://[<username>:<password>@]<IP>[:<PORT>]/stream -frames:v 1 screenshot_%03d.jpg

$ ffmpeg -rtsp_transport tcp -i rtsp://camera_ip:554/stream -vf "fps=1/10" -strftime 1 "screenshot-%Y%m%d-%H%M%S.jpg"
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/B - Vulnerability Assessment/0x03 - Network Ports/IoTs/CCTV/RTSP|Vulnerability Assessment: RTSP]]

### Hackers Arise

- [Hackers Arise: IP Camera Hacking - The FFmpeg Tool for Streaming Camera Video](https://hackers-arise.com/ip-camera-hacking-the-ffmpeg-tool-for-streaming-camera-video/)
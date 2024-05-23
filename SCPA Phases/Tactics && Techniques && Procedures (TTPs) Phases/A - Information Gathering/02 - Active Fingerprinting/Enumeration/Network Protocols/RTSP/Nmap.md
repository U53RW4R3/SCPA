# Nmap

Retrieve RTSP methods.

```
$ nmap -p 554 -Pn --script rtsp-methods <IP>
```

Bruteforce RTSP URLs.

```
$ nmap -p 554 -Pn --script rtsp-url-brute <IP>
```

Enumerate RTSP.

```
$ nmap -p 554 -Pn --script rtsp-methods,rtsp-url-brute <IP>
```
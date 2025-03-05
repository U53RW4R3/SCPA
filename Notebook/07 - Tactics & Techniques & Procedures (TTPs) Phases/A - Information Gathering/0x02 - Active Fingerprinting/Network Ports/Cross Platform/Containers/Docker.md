# Docker

## 01 - Banner Grab

```
$ nmap -p 2375 -Pn -sV <IP>
```

## 02 - Enumerate Version

```
$ docker -H <IP>:2375 version
```

## 03 - Enumerate Images

```
$ docker -H <IP>:2375 images
```

## 04 - Enumerate Processes

```
$ docker -H <IP>:2375 ps -a
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x00 - Exploitation/0xF - Remote Services Exploitation/Network Ports/Containers/Docker]]

### Hacking Articles

- [Hacking Articles: Docker for Pentester - Abusing Docker API](https://www.hackingarticles.in/docker-for-pentester-abusing-docker-api/)
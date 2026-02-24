# 02 - Knock Ports

## Manual

```
$ for port in 4000 2000 6000; do nc <IP> $port; done
```

## #knock

Knock the ports through a specific sequence.

```
$ knock -v <IP> 4 27391 159

$ knock -uv <IP> 4 27391 159
```

You can specify the protocols to each port.

```
$ knock -v <IP> 4:udp 27391:tcp 159:udp
```

## #hping

```
# for port in 4000 2000 6000; do hping3 -c 1 -S 10.10.10.13 -p $port; done
```

## #network-mapper 

```
$ for port in 4000 2000 6000; do nmap -Pn --host-timeout 201 --max-retries 0 -p $port <IP>; done
```
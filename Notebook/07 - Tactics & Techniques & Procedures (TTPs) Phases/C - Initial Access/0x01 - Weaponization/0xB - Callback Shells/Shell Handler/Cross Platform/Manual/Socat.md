# Socat

Checking a remote connection with verbosed debug.

```
$ socat -dddd - tcp4:<remote_IP>:<remote_PORT>
```

Note: Using root privileges to bind a listener to ports below 1024.

## 01 - Reverse Shell

```
$ socat file:`tty`,raw,echo=0 tcp-listen:<PORT>

$ socat -d -d TCP4-LISTEN:443 STDOUT
```

## 02 - Bind Shell

TODO: Make another shell handler for UDP

```
$ socat file:`tty`,raw,echo=0 tcp:<target_IP>:<target_PORT>
```

### 2.1 - Encrypted Bind Shell

```
$ socat - OPENSSL:<target_IP>:<target_PORT>,verify=0
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Shells/One-Liners/Linux/Reverse Shells/Socat|Socat: Reverse Shell]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Shells/One-Liners/Linux/Bind Shells/Socat|Socat: Bind Shell]]
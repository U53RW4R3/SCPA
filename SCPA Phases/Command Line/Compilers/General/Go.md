# Go

Search Tag(s): #command-line #compiler #go #linux #windows

## 01 - Install Go compiler

```
$ wget https://go.dev/dl/go1.22.5.linux-amd64.tar.gz && \
tar -C /usr/local/ -xzf go1.22.5.linux-amd64.tar.gz && \
echo "export PATH=\$PATH:/usr/local/go/bin" >> ~/.bashrc
```

## 02 - Cross compile windows binary

Create a directory to initialize the module.

```
$ mkdir project && cd project

$ go mod init <module_name>
```

Cross compile.

```
$ GOOS=windows GOARCH=amd64 go build .
```

---
## References

- [Go Language](https://go.dev/dl/)
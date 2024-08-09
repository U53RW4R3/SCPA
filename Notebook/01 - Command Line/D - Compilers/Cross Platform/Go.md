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
$ GOOS=windows GOARCH=amd64 go build -ldflags "-s -w" -o implant.exe .
```

To hide a console window.

```
$ GOOS=windows GOARCH=amd64 go build -ldflags "-s -w -H windowsgui" -o implant.exe .
```

## 03 - Compile binary for IoTs

```
$ dpkg --add-architecture mips

$ GOOS=linux GOARCH=mipsel go build
```

TODO: Fill in the rest

```
$ dpkg --add-architecture powerpc
$ dpkg --add-architecture ppc64el

$ dpkg --add-architecture i386
$ GOOS=darwin GOARCH=386 go build test.go
$ GOOS=windows GOARCH=386 go build test.go
$ GOOS=linux GOARCH=386 go build test.go


> GOOS=darwin GOARCH=amd64 go build test.go
> GOOS=windows GOARCH=amd64 go build test.go
> GOOS=linux GOARCH=amd64 go build test.go



$ dpkg --add-architecture arm64
$ dpkg --add-architecture armel
$ dpkg --add-architecture armhf

$ GOOS=darwin GOARCH=arm GOARM=7 go build test.go
$ GOOS=windows GOARCH=arm GOARM=7 go build test.go
$ GOOS=linux GOARCH=arm GOARM=7 go build test.go
``

---
## References

- [Go Language](https://go.dev/dl/)

- [DH1TW: Cross-Compiling Golang (CGO) Projects](https://dh1tw.de/2019/12/cross-compiling-golang-cgo-projects/)
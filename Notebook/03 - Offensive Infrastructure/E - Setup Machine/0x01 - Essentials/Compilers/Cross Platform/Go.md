---
author(s):
  - Userware
tags:
  - helpers
  - command-line
  - compiler
  - go
  - cross-platform
---
# Go

## 01 - Install Go compiler

## 1.1 - Automated

```
# wget -qO- https://git.io/go-installer.sh | bash

# bash <(curl -sL https://git.io/go-installer)
```

## 1.2 - Manual

```
$ wget https://go.dev/dl/go1.22.5.linux-amd64.tar.gz && \
tar -C /usr/local/ -xzf go1.22.5.linux-amd64.tar.gz && \
echo "export PATH=\$PATH:/usr/local/go/bin" >> ~/.bashrc
```

## 02 - Cross compile windows binary

List the available operating system and architecture.

```
$ go tool dist list
```

Create a directory to initialize the module.

```
$ mkdir project && cd project

$ go mod init <module_name>
```

To add dependencies.

```
$ go get golang.org/x/sys/windows
```

Cross compile.

```
$ GOOS=windows GOARCH=amd64 go build -ldflags "-s -w" -o payload.exe .
```

To hide a console window.

```
$ GOOS=windows GOARCH=amd64 go build -ldflags "-s -w -H windowsgui" -o payload.exe .
```

## 03 - Compile binary for IoTs

```
$ dpkg --add-architecture mips

$ GOOS=linux GOARCH=mipsle go build
```

TODO: Fill in the rest

```
$ dpkg --add-architecture i386
$ dpkg --add-architecture arm
$ dpkg --add-architecture arm64
$ dpkg --add-architecture armel
$ dpkg --add-architecture armhf
$ dpkg --add-architecture powerpc
$ dpkg --add-architecture ppc64el
```

```
$ dpkg --add-architecture i386
$ GOOS=darwin GOARCH=386 go build test.go
$ GOOS=windows GOARCH=386 go build test.go
$ GOOS=linux GOARCH=386 go build test.go

$ dpkg --add-architecture arm
$ GOOS=darwin GOARCH=arm go build test.go
$ GOOS=windows GOARCH=arm go build test.go
$ GOOS=linux GOARCH=arm go build test.go

$ dpkg --add-architecture arm64
$ GOOS=darwin GOARCH=arm go build test.go
$ GOOS=windows GOARCH=arm go build test.go
$ GOOS=linux GOARCH=arm go build test.go

$ dpkg --add-architecture armel
$ GOOS=darwin GOARCH=arm go build test.go
$ GOOS=windows GOARCH=arm go build test.go
$ GOOS=linux GOARCH=arm go build test.go

$ dpkg --add-architecture armhf
$ GOOS=darwin GOARCH=arm go build test.go
$ GOOS=windows GOARCH=arm go build test.go
$ GOOS=linux GOARCH=arm go build test.go
```

---
## References

- [Go Language](https://go.dev/dl/)

- [LLGo](https://github.com/goplus/llgo)

- [kerolloz: go-installer](https://github.com/kerolloz/go-installer)

- [DH1TW: Cross-Compiling Golang (CGO) Projects](https://dh1tw.de/2019/12/cross-compiling-golang-cgo-projects/)

- [asukakenji: Go (Golang) GOOS and GOARCH](https://gist.github.com/asukakenji/f15ba7e588ac42795f421b48b8aede63)
---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - port-scanners
  - rustscan
  - network-mapper
---
# Rustscan

## 01 - Setup

### 1.1 - Package Manager

Install with `cargo` as a universal package manager.

```
$ cargo install rustscan && sudo cp ~/.cargo/bin/rustscan /usr/local/bin/
```

### 1.2 - Compile

Clone the repository and then [[03 - Malware Development/Global Helpers/Compilers/Cross Platform/Rust|compile]] it.

```
$ git clone https://github.com/RustScan/RustScan.git && \
cd RustScan/ && rustup default stable && cargo b -r && \
sudo cp target/release/rustscan /usr/local/bin/
```

### 1.3 - Docker

```
$ sudo docker pull rustscan/rustscan:2.0.1

$ cat ~/.bashrc

alias rustscan='docker run -it --rm --name rustscan rustscan/rustscan:2.0.1'
```

## 02 - Usage

Scan a IP target with a timeout and a batch size.

```
$ sudo rustscan -a <IP> -t 3000 -b 4500
```

Scan list of IP targets.

```
$ sudo rustscan -a ip_targets.txt -t 3000 -b 4500
```

Scan the IP target with greppable output.

```
$ sudo rustscan -a <IP> -g
```

Scan with specified ports.

```
$ sudo rustscan -a <IP> -p 21,22,23,25,53,80,443,445,8080
```

Scan with a range of ports.

```
$ sudo rustscan -a <IP> -t 3000 -b 4500 -r 1-65532
```

Scan with top 1000 ports.

```
$ sudo rustscan -a <IP> -t 3000 --top
```

Nmap arguments

```
$ sudo rustscan -a <IP> -- [nmap arguments]

$ sudo rustscan -a <IP> -- -Pn -n -sVC
```

---
## References

### Source Repositories

- [Rustscan Installation Guide](https://github.com/RustScan/RustScan/wiki/Installation-Guide)

### Docker Hub

- [Rustscan Docker Hub](https://hub.docker.com/r/rustscan/rustscan)
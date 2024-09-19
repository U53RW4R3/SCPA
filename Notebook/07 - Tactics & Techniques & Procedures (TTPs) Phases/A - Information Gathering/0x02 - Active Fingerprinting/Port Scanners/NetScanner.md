# NetScanner

## 01 - Setup

### 1.1 - Package Manager

Install it in a pentest distro. 

```
$ sudo apt install -y netscanner
```

Install it in Arch Linux derivatives.

```
$ sudo pacman --noconfirm -S netscanner
```

Install with `cargo`.

```
$ cargo install netscanner && sudo cp ~/.cargo/bin/netscanner /usr/local/bin/
```

### 1.2 - Compile

```
$ git clone https://github.com/Chleba/netscanner.git &&
cd netscanner && rustup default stable && cargo b -r &&
sudo cp target/release/netscanner /usr/local/bin/
```

## 02 - Usage

```
$ sudo netscanner
```

---
## References

- [NetScanner](https://github.com/Chleba/netscanner)
# Rust

Search Tag(s): #helpers #command-line #compiler #rust #cross-platform

## 01 - Install Rust compiler

Download and execute the installer.

```
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

$ wget -qO- https://sh.rustup.rs | sh
```

After installation append this in your resource file (either `~/.bashrc` or `~/.zshrc`) in the last line.

```
source "$HOME/.cargo/env"
```

## 02 - Install Toolchains

List of toolchains.

```
> rustc --print target-list
```

Install toolchain.

```
$ rustup target add x86_64-pc-windows-gnu

$ rustup target add x86_64-pc-windows-msvc
```

## 03 - Initialize Project

Create a project by initializing a cargo and adding the dependencies.

```
$ cargo init --name <project_name>
cargo add <crate>[@<version>] --features process
```

## 04 - Compile Linux binaries

Compile the binary statically.

```
$ cargo b -r

$ rustc -C target-feature=+crt-static -o payload payload.rs
```

## 05 - Compile Windows binaries from Linux

Select specific toolchain to compile a windows binary.

```
$ cargo b -r --target x86_64-pc-windows-gnu

$ cargo b -r --target x86_64-pc-windows-msvc

$ rustc --target=x86_64-pc-windows-gnu -o payload.exe src/main.rs

$ rustc --target=x86_64-pc-windows-msvc -o payload.exe src/main.rs
```
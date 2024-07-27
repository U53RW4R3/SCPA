# Rust

Search Tag(s): #command-line #compiler

## 01 - Install Toolchains

List of toolchains.

```
> rustc --print target-list
```

Install toolchain.

```
$ rustup target add x86_64-pc-windows-gnu

$ rustup target add x86_64-pc-windows-msvc
```

## 02 - Compile Linux binaries

Compile the binary statically.

```
$ rustc -C target-feature=+crt-static hello.rs
```

## 03 - Compile Windows binaries from Linux

Select specific toolchain to compile a windows binary.

```
$ cargo b -r --target x86_64-pc-windows-gnu

$ cargo b -r --target x86_64-pc-windows-msvc

$ rustc --target=x86_64-pc-windows-gnu src/main.rs

$ rustc --target=x86_64-pc-windows-msvc src/main.rs
```
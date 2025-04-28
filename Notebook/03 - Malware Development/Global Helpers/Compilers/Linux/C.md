# C

Search Tag(s): #helpers #command-line #compiler #linux

## GNU Compiler Collection

Compile to binary

```
$ gcc -fno-stack-protector -zexecstack -static -o payload payload.c

$ gcc -zexecstack -static -o payload payload.c
```

Compile to shared object

```
$ gcc -shared -fno-stack-protector -zexecstack -static -o payload.so payload.c
```

x86 architecture

```
$ gcc -m32 -fno-stack-protector -zexecstack -static -o payload payload.c
```

## CLang

```
$ sudo apt install -y clang
```

Compile to binary

```
$ clang -o payload payload.c
```

---
## References

### Source Repositories

- [Obfuscator LLVM](https://github.com/obfuscator-llvm/obfuscator)
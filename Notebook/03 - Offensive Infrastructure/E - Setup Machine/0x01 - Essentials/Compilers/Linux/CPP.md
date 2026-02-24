# CPP

Search Tag(s): #helpers #command-line #compiler #linux

## GNU Compiler Collection

Compile to binary

```
$ g++ -zexestack -static -o payload payload.cpp
```

Specify architecture

```
$ g++ -m32 -zexestack -static -o payload payload.cpp
```

## CLang

Compile to binary

```
$ clang++ -o payload payload.cpp
```

---
## References

- [[03 - Offensive Infrastructure/E - Setup Machine/0x01 - Essentials/Compilers/Linux/C|Linux Compilers: C]]
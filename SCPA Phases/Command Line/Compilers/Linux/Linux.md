# Linux

Search Tag(s): #command-line #compiler #linux

## 01 - GAS (GNU assembler)

```
$ as --64 shell.s -o shell.o

$ ld -m elf_x86_64 shell.o -o shell
```

- Specify architecture

```
$ as --32 shell.s -o shell.o

$ ld -m elf_i386 shell.o -o shell
```

## 02 - YASM

```
$ yasm -f elf64 shell.asm -o shell.o

$ ld -m elf_x86_64 -o shell shell.o
```

- With debugging

```
$ yasm -g dwarf2 -f elf64 shell.asm -l shell.lst -o shell.o

$ ld -g -m elf_x86_64 -o shell shell.o
```

## 03 - C

- Compile to binary

```
$ gcc -fno-stack-protector -zexecstack -static -o shell shell.c

$ gcc -zexecstack -static -o shell shell.c
```

- Compile to shared object

`$ gcc -shared -fno-stack-protector -zexecstack -static -o shell.so shell.c`

- Specify architecture

`$ gcc -m32 -fno-stack-protector -zexecstack -static -o shell shell.c`

## 04 - C++

- Compile to binary

`$ g++ -zexestack -static -o shell shell.cpp`

- Specify architecture

`$ g++ -m32 -zexestack -static -o shell shell.cpp`
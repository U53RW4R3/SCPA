# NASM

Search Tag(s): #command-line #compiler

## 01 - Linux

### 1.1 - ELF

- Compile Linux binaries

```
$ nasm -f elf32 shell.asm -o shell.o

$ ld -m elf_i386 shell.o -o shell
```

```
$ nasm -f elf64 shell.asm -o shell.o

$ ld -m elf_x86_64 shell.o -o shell
```

### 1.2 - EXE

- Compile Windows binaries in Linux

```
$ nasm -f win64 shell.asm -o shell.obj

$ x86_64-w64-mingw32-gcc -o shell.exe shell.obj
```

```
$ nasm -f win32 shell.asm -o shell.obj

$ i686-w64-mingw32-gcc -o shell.exe shell.obj
```

### 1.3 - DLL

- Compile Windows Dynamic Linked Library in Linux

```
$ nasm -f win64 shellcode.asm -o shellcode.obj

$ x86_64-w64-mingw32-gcc -shared -o shellcode.dll shellcode.obj
```

## 02 - Windows

### 1.1 - EXE

#### 1.1.1 - 64-bit

```
C:\> nasm -f win32 shellcode.asm -o shellcode.obj

C:\> link /SUBSYSTEM:CONSOLE /ENTRY:_start shellcode.obj /OUT:shellcode.exe

C:\> objcopy -O binary shellcode.exe shellcode.bin
```
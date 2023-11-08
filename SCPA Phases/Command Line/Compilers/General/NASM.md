# NASM

- **Compile Linux binaries**

```
$ nasm -f elf32 shell.asm -o shell.o

$ ld -m elf_i386 shell.o -o shell
```

```
$ nasm -f elf64 shell.asm -o shell.o

$ ld -m elf_x86_64 shell.o -o shell
```

- **Compile Windows binaries in Linux**

```
$ nasm -f win64 shell.asm -o shell.obj

$ x86_64-w64-mingw32-gcc -o shell.exe shell.obj
```

```
$ nasm -f win32 shell.asm -o shell.obj

$ i686-w64-mingw32-gcc -o shell.exe shell.obj
```

```
C:\> nasm -f win32 your_assembly_code.asm -o your_assembly_code.obj

C:\> link /SUBSYSTEM:CONSOLE /ENTRY:_start your_assembly_code.obj /OUT:your_shellcode.exe

C:\> objcopy -O binary your_shellcode.exe your_shellcode.bin
```

- **Compile Windows Dynamic Linked Library in Linux**

```
$ nasm -f win64 shell.asm -o shell.obj

$ x86_64-w64-mingw32-gcc -shared -o shell.dll shell.obj
```
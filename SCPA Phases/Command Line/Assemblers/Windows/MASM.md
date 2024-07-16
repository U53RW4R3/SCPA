# MASM

Search Tag(s): #command-line #compiler #windows

- x86_64 architecture

```
C:\> ml64 /c /coff shellcode.asm

C:\> link /SUBSYSTEM:WINDOWS /ENTRY:start /VERSION:4.0 shellcode.obj

C:\> objcopy -O binary shellcode.exe shellcode.bin
```
# C

Search Tag(s): #command-line #compiler #linux

- Compile to binary

```
$ gcc -fno-stack-protector -zexecstack -static -o implant implant.c

$ gcc -zexecstack -static -o implant implant.c
```

- Compile to shared object

`$ gcc -shared -fno-stack-protector -zexecstack -static -o implant.so implant.c`

- x86 architecture

`$ gcc -m32 -fno-stack-protector -zexecstack -static -o implant implant.c`
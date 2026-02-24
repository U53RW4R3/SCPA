# Assembler Code

```
$ msfvenom -p linux/x86/exec cmd=whoami R | ndisasm -u -
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 42 bytes

00000000  6A0B              push byte +0xb
00000002  58                pop eax
00000003  99                cdq
00000004  52                push edx
00000005  66682D63          push word 0x632d
00000009  89E7              mov edi,esp
0000000B  682F736800        push dword 0x68732f
00000010  682F62696E        push dword 0x6e69622f
00000015  89E3              mov ebx,esp
00000017  52                push edx
00000018  E807000000        call 0x24
0000001D  7768              ja 0x87
0000001F  6F                outsd
00000020  61                popa
00000021  6D                insd
00000022  6900575389E1      imul eax,[eax],dword 0xe1895357
00000028  CD80              int 0x80
```
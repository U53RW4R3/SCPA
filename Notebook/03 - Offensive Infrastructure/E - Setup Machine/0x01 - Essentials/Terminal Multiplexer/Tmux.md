---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - terminal-multiplexer
  - tmux
---
# Tmux

Install it according to your package manager.

```
$ sudo apt install -y tmux

$ sudo pacman -S --noconfirm tmux
```

Create new multiplexer session.

```
$ tmux new -s <session_name>
```

List the active sessions.

```
$ tmux ls
```

Attach active multiplexer session.

```
$ tmux attach <session_name>
```

| Key Binding                   | Description                              |
|-------------------------------|--------------------------------------------|
| `CTRL-b + CTRL-d`             | Detach session                             |
| `CTRL-b + c`                  | Create a new window                        |
| `CTRL-b + n`                  | Switch to next window                      |
| `CTRL-b + p`                  | Switch to previous window                  |
| `CTRL-b + <NUMBER>`           | Switch to a window with the given number (0-9) |
| `CTRL-b + w`                  | Display summary of windows in the current session |
| `CTRL-b + %`                  | Split vertically to create a pane          |
| `CTRL-b + "`                  | Split horizontally to create a pane        |
| `CTRL-b + o`                  | Switch to next pane                        |
| `CTRL-b + q`                  | Show pane numbers                          |
| `CTRL-b + {`                  | Move current pane left                     |
| `CTRL-b + }`                  | Move current pane right                    |
| `CTRL-b + z`                  | Destroy the current pane                   |
| `CTRL-b + &` (or `CTRL-b + y`) | Destroy the current window                 |
| `CTRL-b + ALT + arrow`        | Resize the active pane (direction depends on arrow key) |
| `CTRL-b + x`                  | Force kill an unresponsive process in a pane |
| `CTRL-u` (Vim keybinding)     | Page Up (in Vim mode)                      |
| `CTRL-d` (Vim keybinding)     | Page Down (in Vim mode)                    |

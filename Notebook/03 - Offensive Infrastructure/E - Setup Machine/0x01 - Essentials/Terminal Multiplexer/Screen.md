---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - terminal-multiplexer
  - screen
---
# Screen

Install it according to your package manager.

```
$ sudo apt install -y screen

$ sudo pacman -S --noconfirm screen
```

Create new multiplexer session.

```
$ screen -S <session_name>
```

List the active sessions.

```
$ session -ls
```

Attach active multiplexer session.

```
$ session -r <session_name>
```

| Key Binding                   | Description                                                |
| ----------------------------- | ---------------------------------------------------------- |
| `CTRL-a + CTRL-d`             | Detach session                                             |
| `CTRL-a + c`                  | Creates a new window                                       |
| `CTRL-a + n`                  | Switch to next window pane                                 |
| `CTRL-a + p`                  | Switch to previous window pane                             |
| `CTRL-a + <NUMBER>`           | Switch to a window pane with the given number (0-9)        |
| `CTRL-a + w`                  | Display summary of windows in the current session          |
| `CTRL-a + k`                  | Kills the current window                                   |
| `CTRL-a + A`                  | Change the name of the current window                      |
| `CTRL-a + "`                  | List available windows                                     |
| `CTRL-a + l` or `CTRL-a + \|` | Split vertically to create a new pane                      |
| `CTRL-a + S`                  | Split horizontally to create a new pane                    |
| `CTRL-a + <TAB>`              | Switch to next pane                                        |
| `CTRL-a + x`                  | Lock the session with a password (uses your user password) |
| `CTRL-a + X`                  | Destroy the current pane                                   |
| `CTRL-a + \`                  | Destroy the screen session                                 |
| `CTRL-a + ?`                  | Display help                                               |

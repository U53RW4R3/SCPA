# Screen

Search Tag(s): #command-line #terminal-multiplexer #linux

## Setup

```
$ cat screen_config.conf
defshell -bash  
startup_message off  
multiuser on  
defscrollback 10000  
logfile /opt/logs/$USER-screenlog.%H.%n.%Y%m%d-%0c:%s.%t.log  
logfile flush 5  
logtstamp on  
deflog on  
defmonitor on  
caption always "%{= gk}%-Lw%{= bW}%50> %n%f* %t %{-}%+Lw%< %= %{= rk} %H %l %{= gk} %0c:%s %{-}"  
defutf8 on  
activity "Activity in %t(%n)"
```

## Usage

Create new multiplexer session.

```
$ screen -S <session_name>
```

Detach session for GNU `screen`.

```
CTRL-a + CTRL-d
```

List the sessions

```
$ session -ls
```

Attach multiplexer session.

```
$ session -r <session_name>
```

Creates a new window

```
CTRL-a + c
```

`CTRL-a + n` -> next window pane

`CTRL-a + p` -> previous window pane

`CTRL-a + <NUMBER>` -> switch to any window pane between 0-9

`CTRL-a + w` -> Display summary of windows in the current session

`CTRL-a + k` -> kills current window

`CTRL-a + A` -> change the name of the window title

`CTRL-a + "` -> list available windows

`CTRL-a + l (OR) CTRL-a + |` -> Split vertically to create a new pane

`CTRL-a + S` -> Split horizontally to create a new pane

`CTRL-a + <TAB>` -> Switch to next pane

`CTRL-a + X` -> Lock the session with a password (by default it uses your user password of your PC)

`CTRL-a + x` -> Destroy the current pane

`CTRL-a + \` -> Destroy the screen session

Display help.

```
CTRL-a + ?
```

---
## References

- [2daygeek: Automatically Record All Users Terminal Sessions Activity Linux Script Command](https://www.2daygeek.com/automatically-record-all-users-terminal-sessions-activity-linux-script-command/)

- [GNU Screen Cheat Sheet](https://kapeli.com/cheat_sheets/screen.docset/Contents/Resources/Documents/index)
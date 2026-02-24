# Shell Prompt

## Configure Multiplexer

### #tmux

Install a clipboard.

```
$ sudo apt install -y xclip

$ sudo dnf install -y xclip

$ sudo pacman -S --noconfirm xclip
```

Clone the repository.

```
$ git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Create a config file `.tmux.conf`.

```
set -g allow-rename off
set -g history-limit 50000
set -g default-terminal "screen-256color"

# Vim keybindings in copy mode

# set -g mouse on
set-window-option -g mode-keys vi
set-option -s set-clipboard off
bind P paste-buffer
bind-key -T copy-mode-vi v send-keys -X begin-selection
bind-key -T copy-mode-vi y send-keys -X rectangle-toggle
unbind -T copy-mode-vi Enter
bind-key -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel 'xclip -selection clipboard -i'
bind-key -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-pipe-and-cancel 'xclip -selection clipboard -i'
  
run-shell /opt/tmux-logging/logging.tmux

set -g @plugin 'tmux-plugins/tmux-logging'

run '~/.tmux/plugins/tpm/tpm'
```

Then source it.

```
$ tmux source ~/.tmux.conf
```

To reload `tmux` source.

```
CTRL-b + SHIFT + I
```

To save terminal raw output with commands.

```
CTRL-b + SHIFT + ALT + P
```

### #screen

Add this in `.screenrc` resource file

```
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

---
## References

- [Bash Prompt Generator](https://bash-prompt-generator.org)
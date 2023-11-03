# Tmux

## Setup

`$ sudo apt install xclip`

`$ git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`

`$ cat ~/.tmux.conf`

---

```
set -g allow-rename off
set -g history-limit 50000
set -g default-terminal "screen-256color"

# Vim keybindings in copy mode

set -g mouse on
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

`$ tmux source ~/.tmux.conf`

To reload tmux source

`CTRL-b + SHIFT + I`

To save terminal raw output with commands

`CTRL-b + SHIFT + ALT + P`

## Usage

`$ tmux new -s <session_name>`

`CTRL-b + CTRL-d` -> detach session for tmux

`$ tmux ls => list the sessions`

`$ tmux attach <session_name>`

`CTRL-b + c` -> creates a new window

`CTRL-b + n` -> next window

`CTRL-b + p` -> previous window

`CTRL-b + <NUMBER>` -> switch to any window pane between 0-9

`CTRL-b + w` -> Display summary of windows in the current session

`CTRL-b + %` -> Split vertically to create a pane

`CTRL-b + "` -> Split horizontally to create a pane

`CTRL-b + o` -> Switch to next pane

`CTRL-b + q` -> Show pane numbers

`CTRL-b + {` -> Move the current pane left

`CTRL-b + }` -> Move the current pane right

`CTRL-b + z` -> To destroy pane

`CTRL-b + & (OR) CTRL-b + y` -> To destroy window

`CTRL-b + ALT + arrow` -> Resize the active pane

`CTRL-b + x` -> Force kill an unresponsive process in a pane

`CTRL-u` (using vim keybingding) -> Page Up

`CTRL-d` (using vim keybingding) -> Page Down

---
## References

- [Tmux Yank](https://tmux-plugins.github.io/tmux-yank/)

- [Tmux Plugin Management](https://jdhao.github.io/2019/01/17/tmux_plugin_management/)

- [Copy and Paste in Tmux](https://www.rockyourcode.com/copy-and-paste-in-tmux/)

- [Everything you need to know about Tmux Copy Pasting Ubuntu](https://www.rushiagr.com/blog/2016/06/16/everything-you-need-to-know-about-tmux-copy-pasting-ubuntu/)

- [Tmux not Displaying Bash Prompt Colors](https://techantidote.com/tmux-not-displaying-bash-prompt-colors/)
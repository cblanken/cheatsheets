# Tmux

- Set configurations in `~/.tmux.conf`
- Your `<leader>` key can be set in your config file with `set prefix <prefix>`

### Movement
```bash
# Move between panes
<prefix> + arrow key
```

### Panes
Leader shortcuts
```bash
# Split vertically
<leader> %
# Split horizontally
<leader> "
```

Commands
```
# Synchronize input between panes in the current window
set synchronize-panes [on]
# Unsynchronize input between panes in the current window
set synchronize-panes off
```

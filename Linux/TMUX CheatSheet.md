
#tmux

**tmux** is a terminal multiplexer that allows you to run multiple terminal sessions, windows, and panes within a single terminal. The default prefix key is `Ctrl+b`, which must be pressed before most commands.
## Session Management

### Creating Sessions

- `tmux` - Start new session[^2]

- `tmux new -s myname` - Start new session with name[^2]

- `Ctrl+b :new` - Create new session from inside tmux[^10]
### Attaching Sessions

  - `tmux a` (or `tmux attach`) - Attach to last session[^2]

- `tmux a -t myname` - Attach to named session[^2]

- `tmux ls` - List all sessions[^2]

### Session Operations

  - `Ctrl+b d` - Detach from current session[^6]

- `Ctrl+b $` - Rename current session[^6]

- `Ctrl+b s` - Show all sessions[^6]

- `Ctrl+b (` / `)` - Previous/Next session[^6]

### Killing Sessions

- `tmux kill-session -t myname` - Kill specific session[^2]

- `tmux kill-ses -a` - Kill all sessions except current[^6]

- `tmux kill-ses -a -t myname` - Kill all sessions except named[^6]

## Window Management

 ### Window Operations

- `Ctrl+b c` - Create new window[^5]

- `Ctrl+b ,` - Rename current window[^5]

- `Ctrl+b n` / `p` - Next/Previous window[^5]

- `Ctrl+b l` - Last used window[^6]

- `Ctrl+b w` - List all windows[^5]

- `Ctrl+b f` - Find window[^2]

- `Ctrl+b &` - Kill current window[^5]

- `Ctrl+b 0-9` - Switch to window by number[^5]

## Pane Management

### Splitting Panes

 - `Ctrl+b "` - Split pane horizontally[^6]

- `Ctrl+b %` - Split pane vertically[^6]
### Pane Navigation

- `Ctrl+b` + Arrow Keys - Navigate between panes[^6]

- `Ctrl+b o` - Go to next pane[^6]

- `Ctrl+b ;` - Toggle to last pane[^6]

- `Ctrl+b q` - Show pane numbers[^6]

- `Ctrl+b q 0-9` - Go to specific pane number[^6]
### Pane Operations

- `Ctrl+b z` - Toggle pane zoom (full screen)[^6]

- `Ctrl+b x` - Kill current pane[^6]

- `Ctrl+b !` - Convert pane to window[^6]

- `Ctrl+b Space` - Toggle between pane layouts[^6]

- `Ctrl+b {` / `}` - Move pane left/right[^6]
### Pane Resizing

- `Ctrl+b` + Hold Ctrl + Arrow Keys - Resize pane[^7]

- `:resize-pane -D 20` - Resize down by 20[^6]

- `:resize-pane -U 20` - Resize up by 20[^6]

- `:resize-pane -L 20` - Resize left by 20[^6]

- `:resize-pane -R 20` - Resize right by 20[^6]

## Command Mode and Configuration

### Essential Commands

- `Ctrl+b :` - Enter command mode[^6]

- `Ctrl+b ?` - List all shortcuts[^2]

- `tmux source-file ~/.tmux.conf` - Reload configuration[^6]

- `tmux show-options -g` - Show current configuration[^6]
### Copy Mode

- `Ctrl+b [` - Enter copy mode[^7]

- `q` or `Escape` - Exit copy mode[^7]
## Mouse Support
 

To enable mouse support for easier interaction without memorizing shortcuts, add this to your `.tmux.conf`:

  
```

setw -g mouse on

```

  

This enables clicking to select panes, right-click context menus, and mouse wheel scrolling.[^7]

  

## Useful Commands

  

- `tmux info` - Show detailed tmux information[^6]

- `:setw synchronize-panes` - Synchronize input across all panes[^6]

- `:swap-pane -s 3 -t 1` - Swap panes 3 and 1[^6]
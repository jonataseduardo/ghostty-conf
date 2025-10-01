### tmux.nvim → Ghostty Native Features

| tmux.nvim Feature | Ghostty Equivalent |
|------------------|-------------------|
| Clipboard sync | Native clipboard integration |
| Window navigation | Ghostty window management |
| Pane resizing | Ghostty window splitting |
| Session management | Ghostty tabs/windows |

## Key Bindings

### Window Navigation
- `<C-h>`, `<C-j>`, `<C-k>`, `<C-l>` - Navigate between windows
- `<A-h>`, `<A-j>`, `<A-k>`, `<A-l>` - Resize windows

### Terminal Management
- `<C-\>` - Toggle terminal (toggleterm.nvim)
- `<leader>tt` - Open terminal
- `<leader>tf` - Open terminal in current file directory

### Ghostty Terminal Shortcuts
- `Ctrl+Shift+T` - New tab
- `Ctrl+Shift+W` - Close tab
- `Ctrl+Shift+N` - New window
- `Ctrl+Shift+D` - Horizontal split
- `Ctrl+Shift+Shift+D` - Vertical split
- `Alt+1-9` - Switch to tab 1-9
- `Alt+Left/Right` - Switch between tabs

## Configuration Files

- `ghostty.conf` - Ghostty terminal configuration
- `lua/kickstart/plugins/ghostty.lua` - Neovim Ghostty integration
- `lua/kickstart/plugins/toggleterm.lua` - Updated for Ghostty compatibility

## Configuration Setup

**IMPORTANT**: Ghostty looks for its configuration file in a specific location on macOS:
- Expected location: `~/Library/Application Support/com.mitchellh.ghostty/config`
- Your config location: `~/.config/ghostty/config/ghostty.conf`

To link your configuration to the correct location, run these commands:

```bash
# Remove the default config file
rm "~/Library/Application Support/com.mitchellh.ghostty/config"

# Create a symbolic link to your configuration
ln -s "~/.config/ghostty/config/ghostty.conf" "~/Library/Application Support/com.mitchellh.ghostty/config"
```

This allows you to keep your configuration in the `.config/ghostty` directory while ensuring Ghostty can find it.

## Configuration Validation

To verify your configuration is working correctly:

```bash
# Validate configuration syntax
ghostty +validate-config

# Show current configuration
ghostty +show-config | grep -E "(font-family|background|foreground)"
```

## Troubleshooting

If you encounter issues:

1. **Configuration not loading**: Verify the symbolic link exists with `ls -la "~/Library/Application Support/com.mitchellh.ghostty/config"`
2. **Invalid configuration options**: Run `ghostty +validate-config` to check for errors
3. **Terminal colors not working**: Make sure Ghostty is using the config file
4. **Keymaps not working**: Restart Neovim after the configuration changes
5. **Clipboard issues**: Check that Ghostty has clipboard permissions on macOS

## Configuration Notes

- The configuration has been updated to use only valid Ghostty options
- Some tmux-like features may not be available in Ghostty (like advanced pane management)
- Use `ghostty +show-config --default` to see all available configuration options

## Restoring tmux (if needed)

To revert back to tmux:

1. Replace `require 'kickstart/plugins/ghostty'` with `require 'kickstart/plugins/tmux'` in `lua/lazy-plugins.lua`
2. Remove the `ghostty.conf` file
3. Restart Neovim

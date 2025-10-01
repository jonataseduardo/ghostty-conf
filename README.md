# Ghostty Terminal Configuration

A comprehensive Ghostty terminal configuration that provides tmux-like functionality using Ghostty's native features. This configuration includes key bindings, color schemes, and window management capabilities optimized for development workflows.

## Features

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
- `Ctrl+1-9` - Switch to tab 1-9
- `Ctrl+Shift+Left/Right` - Switch between tabs

## Installation

### Prerequisites
- [Ghostty terminal](https://mitchellh.com/ghostty) installed on your system
- macOS, Linux, or Windows

### Setup

1. **Clone this repository:**
   ```bash
   git clone https://github.com/yourusername/ghostty-conf.git
   cd ghostty-conf
   ```

2. **Install the configuration:**

   **On macOS:**
   ```bash
   # Remove the default config file
   rm ~/Library/Application\ Support/com.mitchellh.ghostty/config
   
   # Create a symbolic link to your configuration
   ln -s $(pwd)/config/ghostty.conf ~/Library/Application\ Support/com.mitchellh.ghostty/config
   ```

   **On Linux:**
   ```bash
   # Create config directory if it doesn't exist
   mkdir -p ~/.config/ghostty
   
   # Copy the configuration
   cp config/ghostty.conf ~/.config/ghostty/config
   ```

   **On Windows:**
   ```bash
   # Copy the configuration to Ghostty's config directory
   # Location: %APPDATA%\Ghostty\config
   copy config\ghostty.conf "%APPDATA%\Ghostty\config"
   ```

3. **Validate your configuration:**
   ```bash
   # Validate configuration syntax
   ghostty +validate-config
   
   # Show current configuration
   ghostty +show-config | grep -E "(font-family|background|foreground)"
   ```

## Configuration Files

- `config/ghostty.conf` - Main Ghostty terminal configuration
- `README.md` - This documentation

## Customization

### Font Configuration
The configuration uses JetBrains Mono by default. To change the font:

```ini
font-family = "Your Font Name"
font-size = 12
```

### Color Scheme
The configuration includes a dark theme with Kanagawa-inspired colors. To customize:

```ini
background = #1f1f28
foreground = #dcd7ba
cursor-color = #c8c093
selection-background = #2d4f67
```

### Key Bindings
All key bindings can be customized in the `ghostty.conf` file. See the [Ghostty documentation](https://mitchellh.com/ghostty/docs/config) for available options.

## Troubleshooting

If you encounter issues:

1. **Configuration not loading**: 
   - macOS: Verify the symbolic link exists with `ls -la "~/Library/Application Support/com.mitchellh.ghostty/config"`
   - Linux: Check that the config file exists at `~/.config/ghostty/config`
   - Windows: Verify the config file is in `%APPDATA%\Ghostty\config`

2. **Invalid configuration options**: Run `ghostty +validate-config` to check for errors

3. **Terminal colors not working**: Make sure Ghostty is using the config file

4. **Keymaps not working**: Restart Ghostty after configuration changes

5. **Clipboard issues**: Check that Ghostty has clipboard permissions on your system

## Configuration Notes

- The configuration uses only valid Ghostty options
- Some tmux-like features may not be available in Ghostty (like advanced pane management)
- Use `ghostty +show-config --default` to see all available configuration options
- For Neovim integration, additional plugins may be required

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- [Ghostty Terminal](https://mitchellh.com/ghostty) - The amazing terminal emulator
- [Kanagawa Theme](https://github.com/rebelot/kanagawa.nvim) - Color scheme inspiration
- tmux community - For the key binding patterns
# Yakuake Configuration Guide

A comprehensive guide to configuring Yakuake, the KDE dropdown terminal emulator, via the `yakuakerc` configuration file.

## Table of Contents

- [Overview](#overview)
- [File Location](#file-location)
- [Configuration Syntax](#configuration-syntax)
- [Configuration Sections](#configuration-sections)
  - [Animation](#animation)
  - [Appearance](#appearance)
  - [Dialogs](#dialogs)
  - [Shortcuts](#shortcuts)
  - [Window](#window)
  - [Terminal](#terminal)
  - [Behavior](#behavior)
- [Shortcut Syntax Reference](#shortcut-syntax-reference)
- [Complete Example Configuration](#complete-example-configuration)
- [Troubleshooting](#troubleshooting)
- [References](#references)

---

## Overview

Yakuake is a dropdown terminal emulator for KDE Plasma that provides quick terminal access via a keyboard shortcut (default: F12). It drops down from the top of your screen like a Quake-style console, making terminal access instant and unobtrusive.

The `yakuakerc` file controls all aspects of Yakuake's behavior, from visual appearance to keyboard shortcuts. This guide covers all available configuration options.

---

## File Location

| Location | Description |
|----------|-------------|
| `~/.config/yakuakerc` | User-specific configuration (primary) |
| `/usr/share/config/yakuakerc` | System-wide defaults |
| `/etc/xdg/yakuakerc` | System-wide overrides |

The user configuration file is created automatically when you first customize Yakuake settings. It takes precedence over system-wide defaults.

---

## Configuration Syntax

The `yakuakerc` file uses the **INI format**, which consists of:

- **Sections**: Denoted by `[SectionName]` headers
- **Keys**: Configuration option names
- **Values**: Settings assigned to keys

```ini
[SectionName]
key=value
another-key=another-value
```

### Syntax Rules

1. **Boolean values**: Use `true` or `false`
2. **Numeric values**: Use integers (e.g., `50`, `100`, `3000`)
3. **String values**: Plain text without quotes (e.g., `materia-dark`)
4. **Keyboard shortcuts**: Use KDE shortcut notation (e.g., `Ctrl+Shift+N`)
5. **Comments**: Not officially supported in KDE config files

---

## Configuration Sections

### Animation

Controls the dropdown animation when Yakuake appears and disappears.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `Frames` | Integer | `13` | Number of animation frames for the slide effect. Higher values create smoother animations. |

**Example:**
```ini
[Animation]
Frames=13
```

**Notes:**
- Set to `0` to disable animation entirely (instant show/hide)
- Typical range: 0-25 frames

---

### Appearance

Controls visual styling and effects.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `Blur` | Boolean | `true` | Enable blur effect behind the terminal window (requires compositor support) |
| `Skin` | String | `default` | Name of the visual theme/skin to use |
| `SkinInstalledWithKns` | Boolean | `false` | Indicates if the skin was installed via KDE Store |
| `Translucency` | Boolean | `true` | Enable window transparency |

**Example:**
```ini
[Appearance]
Blur=true
Skin=materia-dark
SkinInstalledWithKns=true
Translucency=true
```

**Available Skins:**
- `default` - Classic Yakuake appearance
- `materia-dark` - Material Design dark theme
- Custom skins can be installed via **Configure Yakuake → Appearance → Get New Skins**

**Notes:**
- Blur and translucency require a compositing manager (KWin, Picom, etc.)
- Some skins may override blur/translucency settings

---

### Dialogs

Controls dialog box behavior.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `FirstRun` | Boolean | `true` | Whether to show the first-run welcome dialog |

**Example:**
```ini
[Dialogs]
FirstRun=false
```

**Notes:**
- Set to `false` to suppress the welcome dialog on startup
- Automatically set to `false` after first launch

---

### Shortcuts

Defines keyboard shortcuts for all Yakuake actions. This is the most commonly customized section.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `toggle-window-state` | Shortcut | `F12` | Show/hide the Yakuake window |
| `new-session` | Shortcut | `Ctrl+Shift+N` | Create a new terminal session |
| `close-session` | Shortcut | `Ctrl+Shift+W` | Close the current session |
| `next-session` | Shortcut | `Shift+Right` | Switch to the next session tab |
| `previous-session` | Shortcut | `Shift+Left` | Switch to the previous session tab |
| `move-session-left` | Shortcut | `Ctrl+Shift+Left` | Move current session tab left |
| `move-session-right` | Shortcut | `Ctrl+Shift+Right` | Move current session tab right |
| `rename-session` | Shortcut | `Ctrl+Alt+S` | Rename the current session |
| `edit-profile` | Shortcut | `Ctrl+Shift+E` | Open profile editor |

**Example:**
```ini
[Shortcuts]
toggle-window-state=F12
new-session=Ctrl+Shift+N
close-session=Ctrl+Shift+W
next-session=Shift+Right
previous-session=Shift+Left
move-session-left=Ctrl+Shift+Left
move-session-right=Ctrl+Shift+Right
rename-session=Ctrl+Alt+S
edit-profile=Ctrl+Shift+E
```

**Disabling a Shortcut:**
To completely disable a keyboard shortcut, set it to `none`:
```ini
[Shortcuts]
toggle-window-state=none
```

---

### Window

Controls window positioning, size, and behavior.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `Height` | Integer | `50` | Window height as percentage of screen height |
| `Width` | Integer | `100` | Window width as percentage of screen width |
| `Position` | String | `Top` | Screen edge position (`Top`, `Bottom`, `Left`, `Right`) |
| `ShowOnAllDesktops` | Boolean | `true` | Show Yakuake on all virtual desktops |
| `KeepOpenOnFocusLost` | Boolean | `false` | Keep window open when focus is lost |
| `HideOnOpenApplication` | Boolean | `true` | Hide Yakuake when another application opens |

**Example:**
```ini
[Window]
Height=50
Width=100
Position=Top
ShowOnAllDesktops=true
KeepOpenOnFocusLost=false
HideOnOpenApplication=true
```

**Notes:**
- `Height` and `Width` are percentages (0-100)
- `Position=Top` is the classic Quake-style dropdown
- `KeepOpenOnFocusLost=true` is useful when copy-pasting between windows

---

### Terminal

Controls terminal emulator behavior (passed to Konsole backend).

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `HistorySize` | Integer | `1000` | Number of lines to keep in scrollback buffer |
| `ScrollbackUnlimited` | Boolean | `false` | Enable unlimited scrollback (ignores HistorySize) |
| `UseKonsoleSettings` | Boolean | `true` | Use Konsole's profile settings for terminal behavior |

**Example:**
```ini
[Terminal]
HistorySize=3000
ScrollbackUnlimited=false
UseKonsoleSettings=true
```

**Notes:**
- When `UseKonsoleSettings=true`, many terminal settings come from your Konsole profile
- Configure Konsole profiles via: **Konsole → Settings → Edit Current Profile**
- Unlimited scrollback can consume significant memory for long-running sessions

---

### Behavior

Controls application behavior and integration.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `FocusFollowsMouse` | Boolean | `false` | Focus terminal when mouse enters window |
| `OpenAfterStart` | Boolean | `false` | Show Yakuake window immediately after login |
| `PulseAudioNotification` | Boolean | `true` | Play sound notification on show/hide |

**Example:**
```ini
[Behavior]
FocusFollowsMouse=false
OpenAfterStart=false
PulseAudioNotification=true
```

**Notes:**
- `OpenAfterStart=true` is useful if you always want terminal access immediately after login
- `FocusFollowsMouse=true` can cause unexpected focus changes; use with caution

---

## Shortcut Syntax Reference

### Key Notation

KDE shortcuts use a specific notation format:

| Key Type | Notation | Examples |
|----------|----------|----------|
| Single key | `Key` | `F12`, `Return`, `Escape`, `Tab` |
| With Ctrl | `Ctrl+Key` | `Ctrl+N`, `Ctrl+C` |
| With Shift | `Shift+Key` | `Shift+Right`, `Shift+F1` |
| With Alt | `Alt+Key` | `Alt+F4`, `Alt+Return` |
| With Meta (Super/Windows) | `Meta+Key` | `Meta+Return`, `Meta+T` |
| Combinations | `Ctrl+Shift+Key` | `Ctrl+Shift+N`, `Ctrl+Shift+T` |

### Special Keys

| Key | Notation |
|-----|----------|
| Arrow keys | `Up`, `Down`, `Left`, `Right` |
| Function keys | `F1` through `F35` |
| Enter/Return | `Return` or `Enter` |
| Escape | `Escape` or `Esc` |
| Backspace | `Backspace` |
| Delete | `Delete` |
| Insert | `Insert` |
| Home/End | `Home`, `End` |
| Page Up/Down | `PageUp`, `PageDown` |
| Tab | `Tab` |
| Space | `Space` |

### Modifier Order

When using multiple modifiers, follow this order:
```
Ctrl+Alt+Shift+Meta+Key
```

**Examples:**
- `Ctrl+Shift+N` ✓ (correct order)
- `Shift+Ctrl+N` ✗ (incorrect order, may not work)

### Disabling Shortcuts

To completely disable a shortcut, use `none`:
```ini
toggle-window-state=none
```

---

## Complete Example Configuration

Here's a comprehensive example with all documented options:

```ini
[Animation]
Frames=13

[Appearance]
Blur=true
Skin=materia-dark
SkinInstalledWithKns=true
Translucency=true

[Dialogs]
FirstRun=false

[Shortcuts]
toggle-window-state=F12
new-session=Ctrl+Shift+N
close-session=Ctrl+Shift+W
next-session=Shift+Right
previous-session=Shift+Left
move-session-left=Ctrl+Shift+Left
move-session-right=Ctrl+Shift+Right
rename-session=Ctrl+Alt+S
edit-profile=Ctrl+Shift+E

[Window]
Height=50
Width=100
Position=Top
ShowOnAllDesktops=true
KeepOpenOnFocusLost=false
HideOnOpenApplication=true

[Terminal]
HistorySize=3000
ScrollbackUnlimited=false
UseKonsoleSettings=true

[Behavior]
FocusFollowsMouse=false
OpenAfterStart=false
PulseAudioNotification=true
```

---

## Troubleshooting

### Configuration Not Taking Effect

1. **Restart Yakuake** after editing the configuration file:
   ```bash
   qdbus org.kde.yakuake /yakuake quit
   yakuake &
   ```

2. **Check file permissions**:
   ```bash
   ls -la ~/.config/yakuakerc
   # Should be readable/writable by your user
   ```

3. **Verify syntax**: Ensure no typos in section names or keys

### Shortcuts Not Working

1. **Check for conflicts**: Another application may be using the same shortcut
2. **Verify notation**: Use correct modifier order (`Ctrl+Shift+Key`)
3. **Global shortcuts**: Some shortcuts may need to be configured in KDE System Settings → Shortcuts

### Blur/Translucency Not Working

1. **Enable compositor**: Ensure KWin compositing is enabled
2. **Check driver support**: Some GPU drivers may not support blur effects
3. **Skin compatibility**: Some skins may override transparency settings

### Reset to Defaults

To reset Yakuake to default settings:
```bash
# Backup current config
mv ~/.config/yakuakerc ~/.config/yakuakerc.backup

# Restart Yakuake (will create new default config)
yakuake &
```

---

## References

### Official KDE Documentation

- [Yakuake Handbook](https://docs.kde.org/stable5/en/yakuake/yakuake/) - Official user documentation
- [Konsole Handbook](https://docs.kde.org/stable5/en/konsole/konsole/) - Terminal backend documentation
- [KDE UserBase - Yakuake](https://userbase.kde.org/Yakuake) - Community documentation

### Source Code

- [Yakuake on KDE Invent](https://invent.kde.org/utilities/yakuake) - Source repository
- [Yakuake KCFG File](https://invent.kde.org/utilities/yakuake/-/blob/master/yakuake.kcfg) - Configuration schema definition

### Related Resources

- [KDE Configuration Files](https://develop.kde.org/docs/use/configuration/) - KDE configuration system overview
- [KDE Bug Tracker - Yakuake](https://bugs.kde.org/buglist.cgi?product=yakuake) - Report bugs and issues

---

## Contributing

Found an error or have a suggestion? Contributions are welcome:

1. Open an issue describing the problem or enhancement
2. Submit a pull request with your changes
3. Follow the existing documentation style

---

*Last updated: February 2026*

# Yakuake Documentation Collection

<div align="center">

[![Yakuake](https://img.shields.io/badge/Yakuake-Dropdown%20Terminal-blue?style=for-the-badge&logo=kde)](https://kde.org/applications/system/org.kde.yakuake)
[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-green?style=for-the-badge)](LICENSE)
[![KDE](https://img.shields.io/badge/Powered%20by-KDE%20Konsole-31a4c4?style=for-the-badge)](https://konsole.kde.org/)

*A comprehensive, community-maintained configuration guide for Yakuake users*

</div>

---

## ✨ What is Yakuake?

**Yakuake** (Yet Another Kuake) is a drop-down terminal emulator for the KDE Plasma desktop environment. Inspired by the console in Quake, Yakuake provides instant terminal access with a single keystroke—perfect for developers, system administrators, and power users.

### Key Features

- 🚀 **Instant Access** - Drop-down terminal with customizable hotkey (default: `F12`)
- 🎨 **Highly Customizable** - Skins, transparency, blur effects, and animations
- 📑 **Tabbed Interface** - Multiple sessions in a single window
- 🎯 **Keyboard-Driven** - Full keyboard navigation and shortcuts
- 🔧 **Scriptable** - D-Bus API for automation
- 🌐 **International** - Available in 50+ languages

---

## 📚 Repository Contents

This repository contains comprehensive documentation for configuring and troubleshooting Yakuake:

| File | Description |
|------|-------------|
| [`yakuakerc-configuration-guide.md`](yakuakerc-configuration-guide.md) | **Main guide** - Complete configuration reference with all settings, troubleshooting, D-Bus scripting, and examples |

### What's Inside the Guide

- ✅ Complete `yakuakerc` configuration reference
- ✅ All settings with types, defaults, and valid values
- ✅ Keyboard shortcut syntax and customization
- ✅ D-Bus scripting examples for automation
- ✅ Troubleshooting for common issues
- ✅ Hidden/undocumented configuration options
- ✅ Complete sample configuration with comments
- ✅ Version history and release notes

---

## 🚀 Quick Start

### Installation

#### Arch Linux
```bash
sudo pacman -S yakuake
```

#### Fedora
```bash
sudo dnf install yakuake
```

#### Ubuntu/Debian
```bash
sudo apt install yakuake
```

#### openSUSE
```bash
sudo zypper install yakuake
```

#### From Source
```bash
git clone https://invent.kde.org/utilities/yakuake.git
cd yakuake
mkdir build && cd build
cmake .. 
make
sudo make install
```

### First Launch

1. Run `yakuake` from your terminal or application launcher
2. Press `F12` to toggle the Yakuake window
3. Configure your preferred settings via **Configure Yakuake** (hamburger menu)

---

## 📖 Using This Guide

### For Beginners

1. Start with the [Configuration Syntax](yakuakerc-configuration-guide.md#configuration-syntax) section
2. Review the [Complete Example Configuration](yakuakerc-configuration-guide.md#complete-example-configuration)
3. Copy the example to `~/.config/yakuakerc` and customize

### For Advanced Users

1. Check [Hidden/Undocumented Options](yakuakerc-configuration-guide.md#hiddenundocumented-options)
2. Explore [D-Bus Scripting](yakuakerc-configuration-guide.md#d-bus-scripting) for automation
3. Review the [Troubleshooting Guide](yakuakerc-configuration-guide.md#troubleshooting-guide) for edge cases

### Common Configurations

#### Classic Quake Style (Default)
```ini
[Window]
Height=50
Width=100
Position=Top
```

#### Compact Side Panel
```ini
[Window]
Height=80
Width=40
Position=Right
```

#### Maximum Screen Usage
```ini
[Window]
Height=90
Width=100
Position=Top
```

---

## 🔧 Configuration Overview

Yakuake stores its configuration in `~/.config/yakuakerc`. The main sections include:

| Section | Purpose |
|---------|---------|
| `Animation` | Dropdown animation frames |
| `Appearance` | Skins, transparency, blur |
| `Dialogs` | First-run dialogs |
| `Shortcuts` | Keyboard shortcuts |
| `Window` | Size, position, behavior |
| `Terminal` | Scrollback, history |
| `Behavior` | Focus, startup, notifications |

For complete details, see the [Configuration Sections](yakuakerc-configuration-guide.md#configuration-sections) in the main guide.

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### Ways to Contribute

1. **Report Issues** - Found a problem? Open an issue
2. **Add Documentation** - Improve explanations or add examples
3. **Share Configurations** - Submit your custom configurations
4. **Translate** - Help localize this documentation
5. **Fix Errors** - Spelling, grammar, or technical corrections

---

## 🔗 Resources & Links

### Official Yakuake Resources

- [Official Website](https://kde.org/applications/system/org.kde.yakuake)
- [Source Code (KDE Invent)](https://invent.kde.org/utilities/yakuake)
- [KDE Bug Tracker](https://bugs.kde.org/buglist.cgi?product=yakuake)
- [KDE UserBase Wiki](https://userbase.kde.org/Yakuake)

### Community Resources

- [Arch Wiki - Yakuake](https://wiki.archlinux.org/title/Yakuake)
- [D-Bus Scripting Examples](https://coderwall.com/p/kq9ghg/yakuake-scripting)

### Related KDE Projects

- [Konsole](https://konsole.kde.org/) - The terminal backend Yakuake uses
- [KDE Plasma](https://plasma.kde.org/) - The desktop environment
- [KDE Documentation](https://docs.kde.org/)

---

## 🙏 Acknowledgments

- **KDE Community** - For creating and maintaining Yakuake
- **Contributors** - To this documentation and the broader community

---

<div align="center">

*Last updated: February 2026*

</div>

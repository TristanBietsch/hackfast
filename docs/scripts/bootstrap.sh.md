Bootstrap script automates initial setup.
It installs all tools and configurations.
Run once on a fresh system to get started.

## Purpose

Install all tools listed in `docs/setup & install.md`.
Configure system settings.
Set up dotfiles via GNU Stow.
Reduce manual setup steps to zero.

## Prerequisites

macOS system.
Homebrew installed.
Git installed.
Terminal access.

## Usage

```bash
./bootstrap.sh
```

The script will:
1. Install Homebrew packages (if not already installed)
2. Install GUI applications via Homebrew Cask
3. Clone dotfiles repository
4. Stow dotfiles packages
5. Configure system settings
6. Set up keybinds and shortcuts

## What It Installs

All tools from `docs/setup & install.md`:
- GUIs: Aerospace, Ghostty, Obsidian, Raycast, Shortcat, etc.
- TUIs: nvim, tmux, ranger, lsd, gnu-stow, etc.
- System tools: Karabiner Elements, etc.

## Customization

Edit the script to add or remove packages.
Comment out sections you don't need.
Modify dotfiles stow commands to match your setup.

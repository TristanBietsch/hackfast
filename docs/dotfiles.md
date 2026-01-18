Dotfiles are managed using GNU Stow.
This creates symlinks from a central repository to your home directory.
Each tool or application has its own directory.
Stow handles the symlink creation and removal.

Repository: https://github.com/TristanBietsch/dotfiles

## Structure

Each directory in the dotfiles repository represents one package.
Package names match the tool or application they configure.
For example, `nvim/` contains Neovim configuration files.

## Usage

Install a package:
```bash
stow nvim
```

This creates symlinks from `~/dotfiles/nvim/.config/nvim` to `~/.config/nvim`.

Remove a package:
```bash
stow -D nvim
```

This removes the symlinks without deleting the source files.

## Philosophy

One directory per tool.
Composable and modular.
Easy to add or remove configurations.
Version controlled in a single repository.

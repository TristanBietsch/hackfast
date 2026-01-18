OpenBSD is a security-focused unix-like OS. minimal, clean, keyboard-friendly by default.

---

## download

get the install image from https://www.openbsd.org/faq/faq4.html#Download

for UTM on arm64 mac:
- use `install76.iso` (or latest version) for **arm64** if virtualizing
- use `install76.iso` for **amd64** if emulating x86

---

## install in UTM

1. create new VM in UTM (see [[utm]])
2. choose **Emulate** > Other (for amd64) or **Virtualize** > Other (for arm64)
3. allocate RAM (1-2GB minimum), CPU (1-2 cores), storage (8GB+ recommended)
4. attach OpenBSD ISO as boot drive
5. start VM

---

## installation

boot from ISO, then:

1. `(I)nstall` at prompt
2. choose keyboard layout
3. set hostname
4. configure network (usually `vio0` for virtio)
5. set root password
6. create user account
7. select disk, use `(W)hole disk` and `(A)uto layout`
8. select install sets (defaults are fine)
9. reboot, remove ISO

---

## post-install

### enable doas (sudo alternative)

```bash
echo "permit persist :wheel" > /etc/doas.conf
```

### install packages

```bash
pkg_add vim git tmux curl
```

### set up shell

```bash
pkg_add zsh
chsh -s /usr/local/bin/zsh
```

---

## keyboard-first setup

OpenBSD is already minimal. for a hackfast-style workflow:

```bash
pkg_add \
  neovim \
  tmux \
  ranger \
  htop \
  git
```

### optional: cwm (keyboard-driven window manager)

OpenBSD includes `cwm` by default. minimal tiling/stacking WM with vim-like bindings.

edit `~/.cwmrc`:

```
bind-key CM-h      window-move-left
bind-key CM-j      window-move-down
bind-key CM-k      window-move-up
bind-key CM-l      window-move-right
bind-key CM-Return terminal
bind-key CM-d      menu-exec
```

---

## docs

- https://www.openbsd.org/faq
- https://man.openbsd.org
- https://www.openbsd.org/pkg.html

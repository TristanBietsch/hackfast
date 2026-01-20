# FreeBSD setup

part 3: VM installed, SSH working, now configure dev environment.

---

## prerequisites

- FreeBSD installed (see [freebsd-install](freebsd-install.md))
- SSH working (see [freebsd-ssh](freebsd-ssh.md))
- logged in as your user

---

## 1. enable internet access

SSH uses Emulated VLAN (for port forwarding) but that has no internet.
add a second adapter for internet access.

### problem

- **Emulated VLAN** = port forwarding works, no internet
- **Shared Network** = internet works, no port forwarding

### solution: use both

#### UTM configuration

1. stop VM
2. right-click VM → Edit
3. go to **Devices** section

**adapter 1 (keep existing):**
- Network Mode: Emulated VLAN
- Port Forward: TCP, guest 22 → host 2222

**adapter 2 (add new):**
1. click **New...** below Sound in sidebar
2. select **Network**
3. set Network Mode: **Shared Network**
4. save

#### FreeBSD configuration

after boot, check interfaces:

```bash
ifconfig
```

you should see `vtnet0` and `vtnet1`.

if the new interface has no IP:

```bash
# as root
su -

# get IP via DHCP
dhclient vtnet1

# make permanent
sysrc ifconfig_vtnet1="DHCP"
```

#### verify internet

```bash
ping -c 3 1.1.1.1
```

#### result

| adapter | mode           | purpose         |
| ------- | -------------- | --------------- |
| vtnet0  | Emulated VLAN  | SSH via :2222   |
| vtnet1  | Shared Network | internet access |

---

## 2. become root

```bash
su -
```

---

## 3. bootstrap pkg

```bash
pkg bootstrap
pkg update
pkg upgrade -y
```

---

## 4. install core tools

```bash
pkg install -y \
    git \
    curl \
    wget \
    sudo \
    zsh \
    tmux \
    stow \
    htop \
    tree \
    fzf \
    ripgrep \
    fd-find \
    jq \
    ranger \
    w3m
```

---

## 5. install editors

```bash
pkg install -y vim

# neovim (may not be available on aarch64)
pkg install -y neovim || echo "neovim not in pkg, build from ports"
```

---

## 6. install languages

### go

```bash
pkg install -y go
go version
```

### node

```bash
pkg install -y node npm
node --version
npm --version
```

### typescript

```bash
npm install -g typescript ts-node
```

### python

```bash
pkg install -y python3 py311-pip
```

### rust

```bash
pkg install -y rust
```

---

## 7. configure sudo

```bash
visudo
# uncomment: %wheel ALL=(ALL) ALL
```

test:

```bash
exit  # back to user
sudo whoami  # should print: root
```

---

## 8. set default shell

```bash
chsh -s /usr/local/bin/zsh
```

logout and back in for it to take effect.

---

## 9. install extra tools

some tools need cargo/npm/go:

```bash
# lsd (modern ls)
cargo install lsd

# fast-cli (speed test)
npm install -g fast-cli

# obsidian-cli
go install github.com/Yakitrak/obsidian-cli@latest
```

---

## 10. shell aliases

add to `~/.zshrc`:

```bash
# tools
alias ls="lsd"
alias ll="ls -la"
alias la="ls -a"
alias top="htop"
alias vim="nvim"
alias files="ranger"
alias web="w3m"
alias speed="fast"

# git
alias g="git"
alias gs="git status"
alias gc="git commit"
alias gp="git push"
alias gl="git log --oneline"

# nav
alias ..="cd .."
alias ...="cd ../.."
```

reload:

```bash
source ~/.zshrc
```

---

## 11. dotfiles with stow

```bash
git clone https://github.com/yourusername/dotfiles.git ~/.dotfiles
cd ~/.dotfiles
stow nvim
stow tmux
stow zsh
```

---

## verify

```bash
git --version
go version
node --version
npm --version
python3 --version
rustc --version
tmux -V
```

---

## package reference

| tool     | pkg name   | fallback             |
| -------- | ---------- | -------------------- |
| git      | git        | -                    |
| tmux     | tmux       | -                    |
| vim      | vim        | -                    |
| neovim   | neovim     | ports                |
| go       | go         | -                    |
| node     | node       | -                    |
| python   | python3    | -                    |
| rust     | rust       | -                    |
| htop     | htop       | -                    |
| lsd      | -          | cargo install lsd    |
| stow     | stow       | -                    |
| ranger   | ranger     | -                    |
| fzf      | fzf        | -                    |
| ripgrep  | ripgrep    | -                    |
| fast-cli | -          | npm install -g fast  |

---

## notes

- aarch64 has fewer binary packages than amd64
- use `pkg search <name>` to check availability
- cargo/go/npm fill gaps for missing packages

---

## docs

- https://docs.freebsd.org/en/books/handbook/ports/
- https://www.freshports.org/
- https://pkg.freebsd.org/

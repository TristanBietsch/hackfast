FreeBSD is a unix-like OS known for performance and clean design. great for servers and keyboard-driven workflows.

---

## download

get the install image from https://www.freebsd.org/where/

for UTM on arm64 mac:
- use `FreeBSD-XX.X-RELEASE-arm64-aarch64-disc1.iso` if virtualizing
- use `FreeBSD-XX.X-RELEASE-amd64-disc1.iso` if emulating x86

---

## install in UTM

1. create new VM in UTM (see [[utm]])
2. choose **Emulate** > Other (for amd64) or **Virtualize** > Other (for arm64)
3. allocate RAM (1-2GB minimum), CPU (1-2 cores), storage (8GB+ recommended)
4. attach FreeBSD ISO as boot drive
5. start VM

---

## installation

boot from ISO, then:

1. select `Install` at boot menu
2. choose keyboard layout
3. set hostname
4. select optional components (ports, src)
5. configure network (usually `vtnet0` for virtio)
6. set root password
7. create user account, add to `wheel` group
8. partition disk (Auto UFS or ZFS)
9. reboot, remove ISO

---

## post-install

### enable sudo

```bash
pkg install sudo
visudo  # uncomment %wheel ALL=(ALL) ALL
```

### install packages

```bash
pkg install vim git tmux curl
```

### set up shell

```bash
pkg install zsh
chsh -s /usr/local/bin/zsh
```

---

## keyboard-first setup

for a hackfast-style workflow:

```bash
pkg install \
  neovim \
  tmux \
  ranger \
  htop \
  git
```

---

## docs

- https://docs.freebsd.org/en/books/handbook/
- https://www.freebsd.org/cgi/man.cgi
- https://www.freshports.org

UTM is a virtualization app for macOS.
run other operating systems (linux, bsd, windows) in a VM.

---

## install

```bash
brew install --cask utm
```

or download from https://mac.getutm.app

---

## create a vm

1. open UTM
2. click `+` to create new VM
3. choose **Virtualize** (arm64 guests) or **Emulate** (x86 guests)
4. select OS type or use custom ISO
5. configure RAM, CPU cores, storage
6. attach ISO to boot drive
7. start VM and install OS

---

## tips

- use **Virtualize** when possible (much faster than emulation)
- arm64 macs can virtualize arm64 linux/bsd natively
- for x86 guests (most linux distros, windows), use **Emulate**
- shared directories: Settings > Sharing > enable Directory Sharing

---

## keybinds

| cmd              | action                |
| ---------------- | --------------------- |
| `cmd + q`        | quit UTM              |
| `cmd + w`        | close VM window       |
| `cmd + ,`        | preferences           |
| `ctrl + opt + ←` | release mouse capture |

---

## docs

- https://docs.getutm.app
- https://mac.getutm.app/gallery (pre-built VMs)

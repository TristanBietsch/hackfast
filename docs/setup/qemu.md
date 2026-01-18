QEMU is a terminal-based virtualization tool. once you're comfortable with UTM, you can use QEMU directly for more control and scriptability. UTM is actually a GUI wrapper around QEMU.

---

## install

```bash
brew install qemu
```

---

## basic usage

```bash
# create a disk image
qemu-img create -f qcow2 disk.qcow2 20G

# boot from ISO (arm64 virtualization)
qemu-system-aarch64 -machine virt -cpu host -accel hvf \
  -m 4G -smp 4 \
  -drive file=disk.qcow2,if=virtio \
  -cdrom alpine.iso -boot d

# boot existing disk
qemu-system-aarch64 -machine virt -cpu host -accel hvf \
  -m 4G -smp 4 \
  -drive file=disk.qcow2,if=virtio
```

---

## tips

- use `qemu-system-aarch64` for arm64, `qemu-system-x86_64` for x86
- `-accel hvf` enables hardware virtualization on macOS
- much more flexible for automation and headless VMs

---

## docs

- https://www.qemu.org/docs/master/

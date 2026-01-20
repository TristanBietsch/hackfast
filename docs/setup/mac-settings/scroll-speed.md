Configure macOS scroll speed to reduce mouse dependency.
Faster scrolling means fewer gestures.
Fewer gestures mean less friction.

## System Settings

Open System Settings → Mouse (or Trackpad).
Adjust scrolling speed slider.
Test and iterate until comfortable.
Higher values reduce the number of scroll gestures needed.

## Terminal Scroll Speed

Some terminal emulators have independent scroll settings.
Ghostty allows per-terminal scroll configuration.
Match terminal scroll speed to system scroll speed for consistency.

## Key Repeat Rate

Faster key repeat makes vim navigation (hjkl) feel responsive.
Affects all apps using key repeat, including Vim, Neovim, terminal UIs.

### Method 1 — System Settings (GUI)

System Settings → Keyboard.
Set **Key repeat rate** → Fast.
Set **Delay until repeat** → Short.

### Method 2 — Defaults (CLI, precise)

```bash
defaults write -g InitialKeyRepeat -int 10
defaults write -g KeyRepeat -int 1
```

Lower = faster.
Typical ranges:

- `InitialKeyRepeat`: 10–15
- `KeyRepeat`: 1–2

Logout/login required.

## Philosophy

Scroll speed is a friction point.
Too slow requires many gestures.
Too fast loses precision.
Find the balance that minimizes gestures while maintaining control.

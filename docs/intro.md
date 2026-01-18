# hackfast

A modular, beginner-friendly guide for operating your machine with minimal interface friction.
Everything is vimish.
A distro for productivity.

## Problem

Each app has its own set of commands.
Pointing devices fragment attention.
Context switching breaks flow.

## Solution

Universal keybinds across every app.
Vim navigation everywhere.
Keyboard-first workflow.

## Why macOS

This works for both macOS and Linux.
The focus here is macOS because it balances usability with customization.

## Why Not Omarchy?

[Omarchy](https://github.com/basecamp/omarchy) is a beautiful project.
Nothing here is a criticism of it.
Different tools for different needs.

That said, here's why hackfast exists:

1. **Platform**: Omarchy is Linux. hackfast is macOS. If you're on a Mac, you stay on a Mac.
2. **Scope**: Omarchy is a full OS distribution. hackfast is a workflow guide. One replaces your system, the other enhances it.
3. **Barrier to entry**: Omarchy requires wiping your drive or dual-booting. hackfast requires `brew install`.
4. **Hardware integration**: macOS has native support for Apple hardware — trackpad gestures, battery optimization, Retina displays, M-series chips. Linux support varies.
5. **Commercial software**: macOS runs commercial apps natively — Adobe, Microsoft Office, Figma, Final Cut. Linux requires workarounds or alternatives.
6. **Reversibility**: hackfast changes are symlinks and configs. Undo with `stow -D`. Switching OS is a larger commitment.
7. **Time investment**: Installing and configuring a new OS takes hours to days. hackfast runs a bootstrap script.
8. **Existing ecosystem**: If you already use iCloud, iMessage, AirDrop, Handoff — hackfast preserves that. Omarchy doesn't.
9. **Target audience**: Omarchy is for people who want opinionated Linux. hackfast is for people who want keyboard-first macOS.
10. **Philosophy**: Both follow Unix philosophy, but differently. hackfast is more strictly composable — small tools, plain text, pipes and scripts.

## Best of Both Worlds

Want a real Unix environment?
Run [OpenBSD in a VM](setup/openbsd.md) via UTM.
SSH in from your terminal.
Get the purity of Unix when you need it, macOS as your daily driver.

## Motivation

Modern interfaces optimize for pointing devices.
They fragment attention through small, frequent interactions.

During focused work, these interruptions matter.
Reaching for a mouse, switching context, locating UI elements, or breaking hand position introduces friction between thought and execution.

This project started from a simple observation: flow breaks are often caused by interface mechanics, not by the work itself.

## Background

The transition began with a split keyboard.
That reduced physical friction.
Learning Vim later reduced navigational friction.

The larger realization came afterward: if deep work depends on uninterrupted thought, then the interface must impose zero unnecessary transitions.

Keyboard-first tools already exist.
Most applications already expose shortcuts.
What was missing was a coherent, learnable system that ties everything together.

## Goal

Provide a practical path to a keyboard-only workflow:

- Minimal hand movement
- Minimal thinking
- Maximum speed
- No dependency on a mouse or trackpad
- Predictable, composable shortcuts
- Fast to set up
- Easy to learn incrementally

Keyboard-only does not mean rigid or extreme.
It means removing friction wherever possible.

## Result

After focused iteration and refinement, this repository emerged.

moltbot is an open-source personal AI assistant that runs on your machine.
talk to it via WhatsApp, Telegram, Discord, Slack, Signal, or iMessage.

formerly known as clawdbot.

---

## what it does

- persistent memory - remembers you across conversations
- browser control - browses the web, fills forms, extracts data
- system access - reads/writes files, runs shell commands
- extensible - add community skills or build your own

---

## install

```bash
# one-liner install
curl -fsSL https://molt.bot/install.sh | bash

# start onboarding
clawdbot onboard
```

---

## running in a vm

moltbot has full system access by design. if you want isolation:

- agent can't affect your main system
- sandboxed shell commands and file access
- easy to snapshot and restore

see [vm setup](../setup/vm/utm.md) to run moltbot in its own environment.

---

## links

- https://molt.bot
- https://github.com/moltbot/moltbot

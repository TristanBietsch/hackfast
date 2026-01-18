# Desktops

Aerospace manages window workspaces.
Each workspace is bound to a number key.
Press `opt + num` to switch to that workspace.
Apps are parked in specific workspaces for quick access.

## Workspace Layout

| num | app                   | workspace          |
| --- | --------------------- | ------------------ |
| 1   | obsidian              | notes              |
| 2   | ghostty               | dev                |
| 3   | cursor                | light work         |
| 4   | chatgpt + claude      | ai tools           |
| 5   | UTM                   | reserved           |
| 6   | fantastical + todoist | calendar and tasks |
| 7   | mail                  | email              |
| 8   | beeper                | messages           |
| 9   | spotify / ncspot      | music              |
| 0   | zen                   | browser            |

## Dev Workspace

Workspace 2 is dedicated to development.
Use TMUX to manage sessions.
It typically runs:

| num | app                            | purpose              |     |
| --- | ------------------------------ | -------------------- | --- |
| 0   | btop                           | see system resources |     |
| 1   | files (ranger)                 | nav files            |     |
| 2   | ai (claude pane + gemini pane) | use ai in one window |     |
- nvim for editing
- ranger for file navigation
- btop for system monitoring
- ollama or opencode for AI assistance
- scratch buffers for quick notes

tmux is used only for dev work.
Other workspaces use native application windows.

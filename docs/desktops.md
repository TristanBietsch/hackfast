Aerospace manages window workspaces.
Each workspace is bound to a number key.
Press `leader + num` to switch to that workspace.
Apps are parked in specific workspaces for quick access.

## Workspace Layout

| num | app                      | workspace                                   |     |
| --- | ------------------------ | ------------------------------------------- | --- |
| 1   | obsidian                 | notes (replace w nvim?)                     |     |
| 2   | ghostty                  | dev work (usually running tmux + nvim, etc) |     |
| 3   | cursor                   | light work                                  |     |
| 4   | chatgpt + claude windows | ai client apps and other agent tools        |     |
| 5   |                          |                                             |     |
| 6   | fantastical + todoist    | business cal and todo list for the day      |     |
| 7   | mail                     | apple default email client                  |     |
| 8   |                          |                                             |     |
| 9   | spotify / ncspot         | music                                       |     |
| 0   | zen                      | internet browser                            |     |

Workspace 2 is dedicated to development.
It typically runs:
- tmux for terminal multiplexing
- nvim for editing
- ranger for file navigation
- btop for system monitoring
- ollama or opencode for AI assistance
- scratch buffers for quick notes

tmux is used only for dev work.
Other workspaces use native application windows.

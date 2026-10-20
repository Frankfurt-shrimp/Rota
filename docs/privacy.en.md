# Privacy

[← Back to the README](../README.en.md) ｜ [繁體中文](privacy.md)

**In one line**: Rota records only when an AI starts and stops a turn. Everything stays on your Mac. It never reads content and never uploads anything.

## What Rota records

| Recorded | Why |
|---|---|
| The Session's identifier and whether it is Claude Code or Codex | To tell Sessions apart |
| When each turn starts and stops | To move cards, keep time and show completion |
| **How many** background tasks are running, and of **which kind** (for example subagent or shell) | To know whether a turn has really finished |
| Whether the Session started in a Rota terminal | To suggest linking a card (stored only as a one-way hash) |
| The projects, cards and links you create | The board itself |

## What Rota never records

- Your prompts, the AI's replies or conversations;
- Code, file contents, or tool input and output;
- Background task descriptions, commands or URLs;
- Accounts, email addresses, API keys or any credentials.

Data from the hooks is filtered before anything reaches the disk, so none of the above is ever stored.

The one exception is the attachment tray: for about 1.5 seconds after you drop or paste an image into a Rota terminal, Rota looks at the screen around the terminal's input line for the `[Image #N]` marker Claude Code or Codex shows, and uses it to name the tray item and its preview. While the tray holds attachments that have not been sent, Rota looks at the same area every 0.25 seconds, comparing it only with the paths Rota itself typed and those `[Image #N]` markers, to tell whether you deleted an attachment from the input line — if you did, it leaves the tray. To recognise a deletion Rota briefly remembers a few characters on either side of the attachment, in memory only and only to compare. Nothing else on screen is kept, logged or sent anywhere.

## Where the data lives

On your Mac only:

```
~/Library/Application Support/Shiftboard/
```

("Shiftboard" is Rota's internal name.)

Rota has no server, no analytics and no crash reporting. Its only network-related activity:

- **Claude usage** (only if you turn on Account usage): provided by Claude Code's own status line; Rota reads only the usage numbers;
- **Codex usage**: read through the Codex CLI on your Mac; Rota itself does not connect to the network;
- **Running an app on a phone without a cable** (only when you use it): connects over your local network to your own iPhone or Android phone;
- **Automatic updates** (can be turned off in Settings → Advanced & Diagnostics → Updates): when Rota opens, it reads version information from GitHub; when there is a new version, it downloads the installer from GitHub and verifies its signature before installing. As with any download, GitHub sees your IP address and Rota's version; nothing else is sent.

## Settings files it changes

| File | Change |
|---|---|
| `~/.claude/settings.json` | Rota's hook entries; the status line too if you turn on Account usage |
| `~/.codex/hooks.json` | Rota's hook entries |

Each file is backed up before it changes. **Uninstall** removes only Rota's own entries.

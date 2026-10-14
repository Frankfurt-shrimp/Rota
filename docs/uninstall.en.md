# Removing Rota completely

[← Back to the README](../README.en.md) ｜ [繁體中文](uninstall.md)

Do these **in order**. If you delete the app first, the hook entries Rota added stay in Claude Code's and Codex's settings files.

## 1. Uninstall the integration

1. Open Rota and go to **Settings → Agent Integrations**.
2. Press **Uninstall** under Claude Code and under Codex.
3. If you turned on Account usage, turn it off too; Rota's status line is removed.

Rota removes only its own entries; your other hooks and settings stay as they are. If Rota created `~/.codex/hooks.json` and it holds only Rota's entries, the file is deleted.

## 2. Delete the app

Quit Rota and move `Rota.app` from Applications to the Trash.

## 3. (Optional) Delete your data

If you no longer need your projects, cards and records, press ⇧⌘G in Finder, enter the path below, and move the whole folder to the Trash:

```
~/Library/Application Support/Shiftboard
```

You can also delete:

- Preferences: `~/Library/Preferences/com.franklin.shiftboard.plist`
- App run logs: they are in the `Runs/` folder inside the folder above and go with it.

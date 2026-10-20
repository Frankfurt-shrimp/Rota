# First-time setup

[← Back to the README](../README.en.md) ｜ [繁體中文](setup.md)

Rota learns when an AI starts and stops a turn through Claude Code's and Codex's **hooks**. A hook is a built-in feature of both CLIs that runs a small program at set moments. This page explains what happens during setup.

## 1. Have an AI CLI ready

Install and sign in to at least one:

- **Claude Code**: running `claude` in a terminal starts a conversation.
- **Codex CLI**: running `codex` in a terminal starts a conversation.

## 2. Enable the integration

The first time you open Rota, a **Connect Claude Code and Codex** card appears at the top of the main window. Check **I have stopped all running Codex and Claude Code tasks.**, then press **Agree and Install**. You can also press **Later** and do it in **Settings → Agent Integrations**.

Before anything is written, Rota lists exactly what it will do and waits for you to confirm:

| What it does | Details |
|---|---|
| Adds entries to `~/.claude/settings.json` | Appends Rota's own entries only; your settings and other hooks stay as they are |
| Adds entries to `~/.codex/hooks.json` | The same. If the file does not exist, Rota creates one that holds only its own entries, readable only by you |
| Backs up first | Each file is backed up before it changes, and a failed write is rolled back |
| Installs a small helper | It lives in `~/Library/Application Support/Shiftboard/bin/`; the hooks call it to record start and stop times |

After **Agree and Install**, the card lists what is left to do; press **Done** to close it when you have finished.

> Rota records only those moments. It never reads prompts, code or conversations. See [Privacy](privacy.en.md).

## 3. Codex: approve the new hooks

Codex asks you to approve hooks that were added. After setup, run this once inside Codex:

```
/hooks
```

Follow the prompts to approve Rota's entries. If a later Rota update changes its hooks, Codex may ask again.

## 4. Check that it works

Send one real prompt in Claude Code or Codex. Rota completes the check when the first event arrives, and **Settings → Agent Integrations** shows the integration as **enabled**.

## 5. Start using it

1. Press ＋ in the sidebar to add a project and choose its folder.
2. Press **New Card** on the board.
3. In the form, choose Claude Code or Codex under **Spec by** and **Build by**, then **Save**. Rota opens this card's terminal, starts the Agent and links it to the card by itself.
4. Later, right-click a card and choose **Open Spec and Build…**, or **Open Terminal** for a plain terminal. When you start `claude` or `codex` yourself in a plain one, Rota asks above it whether it is this card's **Spec** or **Build**.

## Optional features

| Feature | Needs |
|---|---|
| Account usage (Claude usage shown in Rota) | Turn it on separately in **Settings → Agent Integrations**; it installs Rota's Claude Code status line |
| Run iOS apps from the toolbar | Xcode; a real device must be paired in Xcode first |
| Run Android apps from the toolbar | Android Studio, or the Android SDK and a JDK |
| Android without a cable | Plug the phone in by USB once and choose **Use Without a Cable** in the destination menu |

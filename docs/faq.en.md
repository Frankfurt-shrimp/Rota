# FAQ

[← Back to the README](../README.en.md) ｜ [繁體中文](faq.md)

## Installing and updating

<details>
<summary>macOS says Rota "cannot be opened" or the developer "cannot be verified"</summary>

Make sure you downloaded the `.dmg` from the [Releases](../../../releases/latest) page. Every release is notarized by Apple and should open normally. If you still see the message, please [report it](../../../issues/new/choose) with a screenshot.
</details>

<details>
<summary>"The integration needs an update" appears after updating</summary>

A new Rota may bring new hooks or a new helper. Press **Update…**, review the list, then press **Update All**. Each file is backed up first. After Codex is updated, you may need to approve once with `/hooks` inside Codex.
</details>

## Linking cards

<details>
<summary>I started <code>claude</code> or <code>codex</code> but no link suggestion appeared</summary>

Check these in order:

1. It was started in a **Rota card terminal**. A `claude` or `codex` you type yourself is asked **Spec** or **Build** above the terminal; one opened from New Card or **Open Spec and Build…** links without asking. The regular Terminal app does not suggest links; its Sessions wait in Unassigned Sessions.
2. In **Settings → Agent Integrations**, that AI is **enabled** and does not need an update.
3. Codex's hooks have been approved with `/hooks`.
4. **When you open Codex, Rota first asks whether it is this card's Spec or Build; sending the first prompt completes the link.** If you chose **Later**, reopen it from **Session pairing** in the terminal's **⋯** menu. Claude Code suggests a link as soon as it opens.
5. Codex in a Rota terminal runs **standalone** (`--no-daemon`) by default, so two Codex terminals in the same project are told apart. In this mode each Codex uses its own memory while open and frees it when it ends; `codex agents` does not list these Sessions; and choosing to keep a task in the background when you quit may not continue it. Only zsh is supported for now. For the shared mode, turn it off in **Settings → Terminal** or type `command codex` in the Rota terminal. In shared mode, if two terminals send a prompt at almost the same time, Rota cannot tell them apart and leaves the Session in **Unassigned** for you to pair by hand. If you open Codex in another terminal app in the same project folder, Rota may suggest that Session in your Rota terminal; check the Session ID in the suggestion.
</details>

<details>
<summary>How do I turn Codex back on after updating Rota?</summary>

1. Open Codex, type `/hooks` and approve Rota's hooks.
2. Quit Codex with `/exit` and **start `codex` again**. A Codex that was already open before the approval does not run the new hooks, so it needs a restart.
3. Send one prompt. Rota completes the check automatically and marks the integration as enabled; there is nothing to confirm in Settings.
</details>

<details>
<summary>How do I quit Codex CLI?</summary>

- Type **`/exit`** (or `/quit`). This is the simplest way.
- Or press **Ctrl+C twice**: the first press stops what it is doing and says "press again to quit"; press again within about a second. Ctrl+D also needs two presses.
- **Esc only interrupts the AI's current work; it does not quit Codex.**
- If work is still running when you quit, Codex asks whether to cancel it, keep it running in the background, or stop it and quit. If you keep it running in the background, Rota treats that Session as ended.
</details>

<details>
<summary>I linked the wrong card or chose the wrong role</summary>

Open the card, unlink the Session in its Sessions section, then link again. Unlinking only removes Rota's record; the AI's Session itself is not affected.
</details>

## Card status

<details>
<summary>A card keeps saying it is waiting for background work</summary>

The AI still has background work running, such as a subagent or a background command. The card completes when it finishes. A *monitor* that only waits for an outside event never holds a card; the card shows "Monitoring" instead.
</details>

<details>
<summary>What do the glow colours mean?</summary>

The colour is the **role of the Session that finished**: blue for Spec, orange for Build. A Session not linked to a card counts as Spec for Codex and Build for Claude Code. You can turn the glow off, or show it only for Sessions linked to a card, in **Settings → Appearance & Layout**.
</details>

## Running apps

<details>
<summary>My iPhone is greyed out and says "Requires iOS xx"</summary>

The app needs a newer iOS than the phone has. Lower it in Xcode under the target → General → Minimum Deployments, or update the phone, then press **Refresh** in the destination menu.
</details>

<details>
<summary>Android without a cable</summary>

1. Plug the phone in by USB and choose **Use Without a Cable** in the destination menu.
2. Unplug it, and connect this Mac to the phone's hotspot or to the same Wi-Fi as the phone.
3. Choose the phone and press ▶︎.

After the phone restarts, plug it in once again. On a shared Wi-Fi you can also use **Pair Android Device with Code…**. On Samsung phones, Auto Blocker can turn off debugging.
</details>

<details>
<summary>I chose an Android project folder but Rota says it is not an app</summary>

Choose the folder that contains `settings.gradle(.kts)` and `gradlew`; Rota also searches above and below it. If the whole project is a single app with no `:app` module, Rota shows it as the **Root project**.
</details>

## Other

<details>
<summary>How do I report a problem?</summary>

Open an [issue](../../../issues/new/choose) with the bug report form. Include your macOS version, your Rota version and a screenshot. Never paste API keys, tokens or other secrets.
</details>

<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="Rota icon">
</p>

<h1 align="center">Rota</h1>

<p align="center">
  <b>A multi-agent board built around Spec-Driven Development (SDD)</b><br>
  Claude Code and Codex work together through spec, build and review. Who is working on what, how far it has got, and who goes next, all on one screen.
</p>

<p align="center">
  <a href="README.md">繁體中文</a> ｜ <b>English</b>
</p>

<p align="center">
  <a href="../../releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/Frankfurt-shrimp/Rota?label=latest"></a>
  <img alt="macOS 15 or later" src="https://img.shields.io/badge/macOS-15%2B-blue">
  <img alt="Notarized by Apple" src="https://img.shields.io/badge/Apple-notarized-success">
</p>

https://github.com/user-attachments/assets/f956e675-ba0a-4541-baae-687fc1f472bd

<p align="center"><sub>The interface in this video is in Traditional Chinese.</sub></p>

<p align="center">
  <a href="../../releases/latest"><b>Download Rota (.dmg)</b></a>
</p>

**Install**: open the downloaded `.dmg` → drag Rota into Applications → open Rota from Applications.

---

## What Rota does

### Work is split the Spec-Driven Development way

<p align="center">
  <img src="assets/flow.en.png" width="720" alt="You create a card → Spec (Claude Code or Codex) → Build (Claude Code or Codex) → You (sign off)">
</p>

In Spec-Driven Development (SDD), you write the spec first, build to the spec, then check the result against it. Rota turns those three stages into three lanes on the board: Spec, Build and You. Each piece of work is a card that moves through them in order.

- **Spec** and **Build** belong to the agents. Claude Code and Codex can each take either one: Codex can write the spec and Claude Code build it, or the other way round.
- **You** is yours: check the result against the spec, then send it back for changes or archive it as done.
- Claude Code and Codex still write the specs and the code. Rota handles who does what and keeps track of it, so you always know whose turn it is and how far it has got.

### Cards follow Claude Code and Codex as they work

<p align="center">
  <img src="assets/board.en.png" width="820" alt="The Rota board with the Spec, Build and You lanes; cards show running, finished and this turn's time">
</p>

- Once a Session is linked, its card moves to that lane when Claude Code or Codex starts working, and is marked finished when the turn ends. You don't drag anything.
- The bottom of each card shows how long this turn took and when it finished. Background work and watching for outside events are shown on the card too.

### When a turn finishes, the edges of your screen light up

<p align="center">
  <img src="assets/glow.en.gif" width="820" alt="When a turn finishes, an orange glow lights the edges of the screen and fades inward">
</p>

- When a turn finishes, the edges of every display glow for a few seconds, then fade out. Blue means a Spec finished, orange means a Build finished.
- The glow never takes keyboard focus and can't be clicked, so it doesn't interrupt what you're doing. With Reduce Motion on, it only fades in and out.
- You can change how long it lasts and which Sessions trigger it, or turn it off, in Settings.

### A built-in terminal that links the Session to a card as it starts

https://github.com/user-attachments/assets/d0ed8a3a-80de-4278-ac65-53a6f51336de

<p align="center"><sub>The interface in this video is in Traditional Chinese.</sub></p>

- Every card can have up to two terminals. The Agents you choose when adding a card link to it by themselves; type `claude` or `codex` in one of the card's terminals and Rota asks above it whether it is this card's Spec or Build.
- Codex is pre-linked before you send the first prompt, and the link completes when you send it. When Rota can't be sure, it asks above the terminal which card to link to.
- **Choose Card…** at the top of the panel lists every card, cards with terminals first; several cards with terminals open never get mixed up.

### Drop images into the terminal and preview them before sending

<p align="center">
  <img src="assets/drop.en.png" width="820" alt="A Rota terminal running Claude Code: the input holds the dropped [Image #1] [Image #2], and the tray in the top-right corner says 2 attachments dropped, with two thumbnails">
</p>

- Drag a screenshot or image into a Rota terminal and it reaches Claude Code or Codex as an attachment, just like dropping a file in Terminal.app. Images dragged from a browser work too.
- An attachment tray appears in the terminal's top-right corner with thumbnails. Click one to open it in Quick Look and check it's the right image before you send.
- Once the Hook confirms the send, the attachments in the tray are marked Sent.

### Run iOS and Android apps from the toolbar

<p align="center">
  <img src="assets/run.en.png" width="820" alt="The Run and Stop buttons in the toolbar, the app to run (iOS App), and the chosen destination (an iPhone 17 Pro simulator)">
</p>

- After you add an app in Project Settings, Run and Stop appear in the toolbar. Destinations include an iPhone, iOS simulators, your Mac, Android phones and Android emulators.
- An Android phone needs a cable only once, to turn on wireless use. After that, runs go over the phone's hotspot or the same Wi-Fi.
- Running an app doesn't use a terminal. One app runs at a time, and Rota asks before switching.

### See Claude Code and Codex usage in the toolbar

<p align="center">
  <img src="assets/quota.en.png" width="480" alt="The usage panel: Claude Code and Codex remaining 5-hour and weekly usage">
</p>

- The usage panel in the toolbar shows the remaining 5-hour and weekly usage for Claude Code and Codex, so you can decide who takes the next turn.
- Claude Code usage has to be turned on separately; see the [guide](docs/guide.en.md#usage).

## Getting started

1. **Add a project**: press **+** in the sidebar and choose the project folder.
2. **Turn on the integrations**: on first launch a **Connect Claude Code and Codex** card appears at the top of the main window. Check **I have stopped all running Codex and Claude Code tasks.**, then press **Agree and Install**. If you use Codex, also run `/hooks` in Codex once to approve. See [First-time setup](docs/setup.en.md).
3. **Add a card**: press **New Card** (⌘N) on the board and write what the work is.
4. **Start Claude Code or Codex**: in the same form, choose Claude Code or Codex under **Spec by** and **Build by**, then **Save**. Rota opens this card's terminal, starts the Agent and links it to the card by itself.
5. **Open more later**: right-click a card and choose **Open Spec and Build…**, pick an Agent for Spec and for Build, and they open already linked. Or choose **Open Terminal** for a plain terminal, type `claude` or `codex`, then choose **Spec** or **Build** above it.

Everything after that, such as running several terminals, linking Sessions you skipped, and setting up app runs and wireless Android, is in the [guide](docs/guide.en.md).

## Guide

| Topic | What it covers |
|---|---|
| [First-time setup](docs/setup.en.md) | Turning on the integrations, approving Codex `/hooks`, checking that it works |
| [Linking cards](docs/guide.en.md#linking-cards) | Linking Claude Code and Codex, Later and Don't, replacing a linked Session, Undo |
| [Unassigned Sessions](docs/guide.en.md#unassigned-sessions) | Sessions started in other terminal apps or not linked yet, and how to link them later |
| [Several terminals at once](docs/guide.en.md#several-terminals-at-once) | Several Claude Code or Codex terminals in one project, and Codex standalone mode |
| [Reading a card](docs/guide.en.md#reading-a-card) | Running, finished, background work, watching, this turn's time, marking a turn interrupted, archiving |
| [Completion glow](docs/guide.en.md#completion-glow) | On and off, duration, linked cards only |
| [Usage](docs/guide.en.md#usage) | Turning on Claude Code account usage, reading the usage panel |
| [Running apps](docs/guide.en.md#running-apps) | Adding an app in Project Settings, destinations, the run log, when an iPhone is greyed out |
| [Wireless Android](docs/guide.en.md#wireless-android) | Hotspot and Wi-Fi, pairing codes, after the phone restarts |
| [Integrations need updating](docs/guide.en.md#integrations-need-updating) | What to do when this appears after updating Rota |


## Privacy and trust

> - **Files it changes**: only `~/.claude/settings.json` and `~/.codex/hooks.json`. Rota adds its own entries only, backs up each file first, and never touches your other hooks.
> - **Never read**: prompts, code, conversations or tool output. The one exception: after you attach an image, Rota reads only the `[Image #N]` marker from the terminal's input line, and keeps nothing else.
> - **Never uploaded**: everything stays on your Mac. No analytics, no server of ours. Only automatic updates read version information from GitHub, and you can turn them off.
> - **Fully removable**: press **Uninstall** in the app and Rota's entries are removed; everything else stays as it was.
>
> Details: [Privacy](docs/privacy.en.md)

## Requirements

| | |
|---|---|
| macOS | 15 or later, Apple silicon or Intel |
| AI CLI | At least one, installed and signed in: [Claude Code](https://docs.anthropic.com/claude-code) or [Codex CLI](https://github.com/openai/codex) |
| Optional: run iOS apps | Xcode |
| Optional: run Android apps | Android Studio (or the Android SDK and a JDK) |

## Updating and removing

- **Update**: from 1.1.0 on, Rota checks for a new version each time it opens, downloads it in the background and installs it when you quit Rota; the board also offers **Restart Now** to update right away. You can turn automatic updates off, or use **Check for Updates…**, in Settings → Advanced & Diagnostics → Updates. To get from 1.0.0 to 1.1.0, download the new `.dmg` from [Releases](../../releases/latest) once and replace Rota; your data is kept. If Rota says the integration needs an update, press **Update…** once.
- **Remove**: uninstall the integration in **Settings → Agent Integrations** first, then delete the app. See [Uninstall](docs/uninstall.en.md).

## FAQ

<details>
<summary>I started <code>codex</code> in a terminal but no link suggestion appeared</summary>

Check that Codex is enabled in **Settings → Agent Integrations** and does not need an update. New Codex hooks must be approved once with `/hooks` inside Codex. More in the [FAQ](docs/faq.en.md).
</details>

<details>
<summary>A card keeps saying "waiting for background work"</summary>

The AI still has work running in the background, such as a subagent or a background command. The card completes when it finishes. A *monitor* that only waits for an outside event never holds a card; the card shows "Monitoring" instead.
</details>

<details>
<summary>My iPhone is greyed out in the destination menu</summary>

The app needs a newer iOS than the phone has; the menu says "Requires iOS xx". Lower Minimum Deployments in Xcode, or update the phone.
</details>

<details>
<summary>Running on an Android phone without a cable</summary>

Plug the phone in by USB once and choose **Use Without a Cable** in the destination menu. After that, connect this Mac to the phone's hotspot or the same Wi-Fi. After the phone restarts, plug it in once again.
</details>

More: [FAQ](docs/faq.en.md)

## Reporting a problem

Open an [issue](../../issues/new/choose) with the bug report form. Include your macOS version, your Rota version (**Rota → About Rota**) and a screenshot. **Never paste API keys or other secrets.**

## Changelog, licence and notices

- [Changelog](CHANGELOG.md)
- [Licence](LICENSE): free to download and use; the source code is not published.
- Rota is an independent project and is not affiliated with OpenAI or Anthropic. Claude and Claude Code are trademarks of Anthropic. Codex is a trademark of OpenAI.

© 2026 Yung Fu Lin. All rights reserved.

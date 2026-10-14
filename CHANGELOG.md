# 更新紀錄 ｜ Changelog

格式：每個版本先寫中文，再寫英文。版本號遵循 `主版本.次版本.修正版`。
Each release lists Chinese first, then English. Versions follow `major.minor.patch`.

## 1.0.0 — 第一個公開版本 ｜ First public release

**中文**

- **看板接力**：「規格／實作／我」三條河道。Claude Code 與 Codex 都可以接任何一棒。
- **連結卡片**：在 Rota 終端機啟動 `claude` 或 `codex` 時，提議連結到卡片，並詢問是規格還是實作。
- **自動移動與完成**：卡片跟著 AI 的進度移動；做完時螢幕邊緣會亮起光暈，顏色代表完成者的角色。可以設定只對已連結的 Session 顯示。
- **背景工作判斷**：只是在等外部事件的「監看」不會讓卡片卡在「等待背景工作」。
- **整合一鍵更新**：新版本帶來新的 hook 時，主視窗會提示，一次就能全部更新，並自動備份。
- **執行 App**：從工具列把 Xcode 或 Android App 執行到模擬器或實機，包含 iPhone 無線，以及 Android 透過手機熱點不接線執行。

**English**

- **Relay board**: three lanes, Spec, Build and You. Claude Code and Codex can each take any turn.
- **Link cards**: start `claude` or `codex` in a Rota terminal and Rota offers to link it to a card, asking whether it is the Spec or the Build.
- **Moves and completion**: cards follow the AI's progress. When a turn finishes, the screen edge glows in the colour of the finishing Session's role. You can limit the glow to linked Sessions.
- **Background work**: a *monitor* that only waits for an outside event no longer leaves a card waiting for background work.
- **One-step integration updates**: when a new version brings new hooks, the main window says so and updates everything at once, with backups.
- **Run apps**: run Xcode or Android apps from the toolbar on simulators and devices, including wireless iPhone runs and cable-free Android runs over the phone's hotspot.

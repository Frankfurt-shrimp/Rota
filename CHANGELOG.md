# 更新紀錄 ｜ Changelog

格式：每個版本先寫中文，再寫英文。版本號遵循 `主版本.次版本.修正版`。
Each release lists Chinese first, then English. Versions follow `major.minor.patch`.

## 1.1.1 — `!` 之後也會完成、額度新舊看圓點 ｜ Turns after `!` complete; quota freshness on the dot

**中文**

### 修正

- **用 `!` 執行指令之後，那一輪也會完成**：在 Claude Code 用 `!` 執行 shell 指令後，模型針對輸出回答的那一輪，Rota 原本看不到結束：卡片不亮光暈、不移動。現在回答完約 5 秒後會完成並亮光暈，Session 紀錄記一次完成；因為 Claude Code 沒有送出開始事件，這一輪的時長顯示為未知。送出訊息後按 Esc、再改用 `!` 時，原本那一輪會一直停在「執行中」，現在會正常完成。Codex 的 `!` 不會開始新的一輪，不受影響。
- **工具列額度的新舊看圓點**：數字前面的橘色時鐘拿掉了，改成看每組前面的圓點：實心是最新，空心圈是舊資料，空心圈加紅點是最近一次讀取失敗（不論上次讀數多舊）。滑鼠停在額度上的說明改成分行顯示，每個服務一段、每個額度一行。

**English**

### Fixed

- **The turn after a `!` command completes**: after running a shell command with `!` in Claude Code, Rota never saw the end of the turn in which the model answers its output: no glow, no move. That turn now completes about 5 seconds after the answer, with the glow, and counts as one completion; its duration shows as unknown, because Claude Code sends no start for it. Sending a message, pressing Esc and then using `!` used to leave that turn on Running; it now completes normally. Codex's `!` does not start a turn and is unaffected.
- **Quota freshness on the dot**: the orange clock before each number is gone. Each group's dot now shows freshness: solid when current, a hollow ring when old, and a hollow ring with a red badge when the latest read failed, however old the reading. The quota Help is laid out in lines: one block per service, one line per window.

## 1.1.0 — 每張卡片有自己的終端機 ｜ Every card gets its own terminals

**中文**

### 新功能

- **卡片終端機**：每張卡片最多可以開兩個終端機，一個寫規格、一個做實作。新增卡片時，在「規格由」「實作由」選 Claude Code 或 Codex，Rota 會開好這張卡片的終端機、啟動 Agent，並自動連結到對應的角色，不用再選卡片。選的 Agent 開不了時，卡片照樣建立，並說明是哪個 Agent、為什麼沒有開；Codex 第一次啟動前，表單會提醒你要信任 Rota 的 hooks。終端機現在都屬於卡片，不再有專案終端機。
- **之後再開**：在卡片上按右鍵，選「一鍵開啟規格與實作…」，選好兩邊的 Agent 就會開好並自動連結；或選「開啟終端機」開一個純終端機，自己輸入 `claude` 或 `codex`，上方會問要連結成這張卡片的「規格」還是「實作」。
- **取代前先確認**：要連結的角色已經連著另一個 Session 時（不論還在執行或已結束），畫面中間會跳出確認視窗，寫出目前連著的 Session 和狀態。預設是「取消」，按 Return 或空白鍵都不會取代。一鍵開啟也一樣。連結被取代的 Session，它的終端機會顯示提示，可以按「重新連結…」再選一次角色。
- **切換卡片**：點一張卡片，或從面板上方的「選擇卡片…」選一張，底部面板就切到這張卡片：有終端機就顯示它的終端機，還沒有就顯示開啟按鈕，按了才會開。「選擇卡片…」最上面是開著終端機的卡片，下面依專案分成子選單；面板上方顯示「專案 › 卡片」，改名時跟著更新。封存卡片時，如果終端機還在執行，會先詢問。
- **終端機並排**：一張卡片開了規格和實作兩個終端機時，視窗夠寬就預設並排顯示，仍可切回分頁。
- **自動更新**：開啟 Rota 時檢查新版本，在背景下載並驗證簽章，結束 Rota 時安裝；看板上的「立即重新啟動」可以馬上更新（會先結束終端機；萬一安裝失敗，Rota 仍是舊版，終端機需要重新開）。可以在「設定 → 進階與診斷 → 更新」關閉。從 1.0.0 升級到 1.1.0 仍需手動下載一次。
- **貼上的圖片也進托盤**：在 Rota 的終端機用 ⌘V 貼上圖片或 Finder 拷貝的檔案，跟拖入一樣會出現在附件托盤；在 Claude Code／Codex 裡按 Ctrl+V 貼圖也會同步進托盤。托盤和預覽的名稱改用終端機顯示的 `[Image #N]`，辨識不到時顯示檔名。
- **從輸入列刪掉附件，托盤也跟著移除**：還沒送出的附件，用 Backspace、Ctrl+U 等方式從輸入列刪掉後，約 0.6 秒內就會從托盤消失；30 秒內復原（undo）會放回托盤。輸入列被權限詢問等畫面蓋住，或往上捲動時，不會移除。分辨不出刪掉的是哪一個時（例如 Codex 重新編號），托盤維持原樣，仍可用 ✕ 移除。
- **終端機文字大小**：「顯示」選單新增 ⌘+／⌘-／⌘0，調整終端機的文字大小。
- **首次設定**：按下「同意並安裝」後，提示卡會留著並列出接下來的步驟（例如 Codex 的 `/hooks` 核准），不會直接消失。

### 修正

- **完成不再漏掉**：Claude Code 做完之後，卡片有時會一直顯示「執行中」，直到下一個事件才完成，也不亮光暈。現在完成約在 Claude 停止後 5 秒成立；偶爾漏掉時，1～2 秒內會自動補上，並且有次數上限，不會一直重試。
- **全螢幕關閉**：在全螢幕按紅色關閉鈕，視窗會直接關閉，不會先回到桌面、要再按一次。關掉最後一個視窗時，Rota 繼續在背景執行；從 Dock 重新打開會回到關閉前的樣子：同一個專案或卡片、同樣的終端機和畫面記錄，不會再顯示「終端機正在另一個視窗使用」。要完全結束請按 ⌘Q。
- **`--resume` 回來會再問**：用 `claude --resume` 或 `codex resume` 回到一個目前沒有連結的 Session（例如連結被取代、撤銷，或之前按了「稍後」），終端機上方會再問一次要不要連結。
- **標題不再閃爍**：切換專案、封存紀錄，或執行 App 時，左上角的專案名稱不會再短暫變成「Rota」。
- **連結清單即時更新**：等待連結卡片時新增的卡片，馬上就會出現在「連結卡片」的清單裡。

### 其他

- **在模擬器執行**：配合 Xcode 27 拿掉 Simulator.app，改為打開 DeviceHub。
- **拿掉不再有作用的設定**：「在 Rota 終端機啟動的 Session 建議連結卡片」已經拿掉。Rota 的終端機都屬於卡片，在裡面自己啟動的 Agent 一律會問要連結成規格還是實作。

**English**

### New

- **Card terminals**: every card can have up to two terminals, one for the spec and one for the build. When you add a card, choose Claude Code or Codex under **Spec by** and **Build by**: Rota opens that card's terminals, starts the Agents and links each to the card in its role — no card to choose. If an Agent can't be opened, the card is still created and Rota says which Agent and why; before Codex's first start, the form reminds you that it will ask you to trust Rota's hooks. Terminals now belong to cards; there are no project terminals any more.
- **Opening again later**: right-click a card and choose **Open Spec and Build…**, pick an Agent for each, and they open already linked. Or choose **Open Terminal** for a plain terminal, start `claude` or `codex` yourself, and Rota asks above it whether it is this card's **Spec** or **Build**.
- **Asking before replacing**: when the role you pick is already linked to another Session — still running or ended — a confirmation appears in the middle of the window, naming that Session and its state. **Cancel** is the default; neither Return nor Space replaces anything. **Open Spec and Build…** asks the same way. A Session whose link was taken shows a notice in its terminal, with **Relink…** to choose a role again.
- **Switching cards**: click a card, or pick one in **Choose Card…** at the top of the panel, and the bottom panel switches to it: its terminals, or buttons to open them — nothing starts until you press one. **Choose Card…** lists the cards with terminals open first, then every project with a submenu of its cards; the panel shows "Project › Card" and follows a rename. Archiving a card whose terminals are still running asks first.
- **Terminals side by side**: a card's Spec and Build terminals open side by side when the window is wide enough; you can still switch back to tabs.
- **Automatic updates**: Rota checks for a new version when it opens, downloads it in the background, verifies its signature and installs it when you quit; **Restart Now** on the board updates right away (it ends your terminals first; if the install ever fails, Rota stays on the old version and the terminals need to be opened again). Turn it off in Settings → Advanced & Diagnostics → Updates. Going from 1.0.0 to 1.1.0 still needs one manual download.
- **Pasted images reach the tray**: ⌘V of an image, or of a file copied in Finder, into a Rota terminal now lands on the attachment tray just like a drop, and Ctrl+V of an image in Claude Code or Codex shows up there too. Tray items and their preview are named after the `[Image #N]` the terminal shows, or the file name when Rota cannot see one.
- **Deleting an attachment from the input takes it off the tray**: an attachment not yet sent that you delete from the input line (Backspace, Ctrl+U…) leaves the tray within about 0.6 seconds; an undo within 30 seconds puts it back. Nothing leaves while the input is covered, for example by a permission prompt, or while you scroll up. When the screen cannot tell which one went — Codex renumbers the rest — the tray stays as it is and ✕ still removes one.
- **Terminal text size**: ⌘+, ⌘- and ⌘0 in the View menu change the terminal's text size.
- **First-time setup**: after **Agree and Install**, the card stays and lists the next steps (such as approving `/hooks` in Codex) instead of disappearing.

### Fixed

- **Completions are no longer missed**: after Claude Code finished, a card could stay "Working" until the next event arrived, without a glow. A completion now stands about 5 seconds after Claude stops; if that check is ever missed, Rota catches up within 1–2 seconds, with a fixed limit on retries.
- **Closing in full screen**: the red close button in full screen now closes the window, instead of first dropping it back on the desktop for a second click. Rota keeps running after its last window closes; opening it again from the Dock brings that window back as it was — the same project or card, the same terminals and their scrollback — instead of saying the terminals are in use in another window. Quit with ⌘Q.
- **`--resume` asks again**: returning to a Session that is not linked now — its link was replaced or undone, or you chose **Later** — with `claude --resume` or `codex resume` brings the question back above the terminal.
- **The title no longer flickers**: switching projects or Archive History, or running an app, no longer flashes "Rota" in place of the project's name.
- **The link list is live**: a card added while a Session waits to be linked appears in **Link Card** right away.

### Other

- **Run on a simulator**: with Xcode 27, which removed Simulator.app, Rota opens DeviceHub instead.
- **A setting that no longer did anything is gone**: **Suggest linking Sessions started in a Rota terminal to a card** has been removed. Rota's terminals all belong to cards, and an Agent you start in one is always asked whether it is Spec or Build.

## 1.0.0 — 第一個公開版本 ｜ First public release

**中文**

- **看板協作**：「規格／實作／我」三條河道。Claude Code 與 Codex 都可以負責任何一段。
- **連結卡片**：在 Rota 終端機啟動 `claude` 或 `codex` 時，提議連結到卡片，並詢問是規格還是實作。
- **自動移動與完成**：卡片跟著 AI 的進度移動；做完時螢幕邊緣會亮起光暈，顏色代表完成者的角色。可以設定只對已連結的 Session 顯示。
- **背景工作判斷**：只是在等外部事件的「監看」不會讓卡片卡在「等待背景工作」。
- **整合一鍵更新**：新版本帶來新的 hook 時，主視窗會提示，一次就能全部更新，並自動備份。
- **執行 App**：從工具列把 Xcode 或 Android App 執行到模擬器或實機，包含 iPhone 無線，以及 Android 透過手機熱點不接線執行。

**English**

- **Shared board**: three lanes, Spec, Build and You. Claude Code and Codex can each take either part.
- **Link cards**: start `claude` or `codex` in a Rota terminal and Rota offers to link it to a card, asking whether it is the Spec or the Build.
- **Moves and completion**: cards follow the AI's progress. When a turn finishes, the screen edge glows in the colour of the finishing Session's role. You can limit the glow to linked Sessions.
- **Background work**: a *monitor* that only waits for an outside event no longer leaves a card waiting for background work.
- **One-step integration updates**: when a new version brings new hooks, the main window says so and updates everything at once, with backups.
- **Run apps**: run Xcode or Android apps from the toolbar on simulators and devices, including wireless iPhone runs and cable-free Android runs over the phone's hotspot.

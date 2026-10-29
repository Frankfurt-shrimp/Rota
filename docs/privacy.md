# 隱私

[← 回到首頁](../README.md) ｜ [English](privacy.en.md)

**一句話**：Rota 只記錄 AI「什麼時候開始、什麼時候結束」一輪工作。所有資料都留在你的 Mac 上，不讀取內容，也不上傳任何東西。

## Rota 記錄什麼

| 記錄 | 用途 |
|---|---|
| Session 的識別碼、屬於 Claude Code 還是 Codex | 分辨是哪一個 Session |
| 每一輪開始與結束的時間 | 移動卡片、計時、顯示完成 |
| 正在背景執行的工作有**幾個**、各是**哪一種**（例如 subagent、shell） | 判斷這一輪是不是真的做完了 |
| 這個 Session 是不是在 Rota 的終端機中啟動 | 提議連結卡片（只存一個無法還原的雜湊值） |
| 你建立的專案、卡片、連結 | 看板本身 |

## Rota 不記錄什麼

- 你的 prompt、AI 的回覆、對話內容；
- 程式碼、檔案內容、工具的輸入或輸出；
- 背景工作的說明文字、指令內容、網址；
- 帳號、Email、API key 或任何登入資訊。

hook 送進來的資料會先經過過濾，上面這些內容在寫入磁碟之前就已經被丟掉。

例外有下面四種，看到或讀到的內容都只在記憶體裡用，不保存、不記錄，也不送到任何地方。

**附件托盤**：你在 Rota 的終端機拖入或貼上圖片之後，Rota 會在約 1.5 秒內查看終端機輸入列附近的畫面，只辨識 Claude Code／Codex 顯示的 `[Image #N]` 標記，用來當托盤和預覽的名稱。托盤上還有沒送出的附件時，Rota 也用同樣的方式每 0.25 秒看一次輸入列附近，只比對 Rota 自己替附件輸入的路徑和 `[Image #N]`，確認附件是否已經從輸入列刪掉，刪掉了就從托盤移除（為了辨認刪除，Rota 會暫時記住附件左右少量相鄰文字，只存在記憶體、只用來比對）。其他文字不保存、不記錄，也不送到任何地方。

**終端機輸入框**：為了不把訊息送進選單，Rota 送出 Codex 的訊息前會看終端機輸入列附近的畫面，確認 Codex 已經回到自己的輸入列；Claude Code 顯示淡色的建議 prompt 時，輸入框也從同一個地方讀出那段提示。附加圖片時，Rota 一樣只辨識 `[Image #N]` 標記，確認圖片進了 Agent 的輸入列再送出文字。

**`/` 清單**：輸入框列出指令和 skill 時，Rota 會讀這些檔案開頭的名稱和說明（每個檔案最多 8 KB，一次最多 500 個檔案）：`~/.claude` 裡的 skill、指令和已啟用外掛的 skill 與指令；Codex 的 `CODEX_HOME`（沒有設定時是 `~/.codex`）和 `~/.agents` 裡的 skill 與 prompt；卡片專案資料夾裡 `.claude`、`.codex`、`.agents` 底下的 skill 和指令。檔案的其他內容不讀。

**↑／↓ 叫回 prompt**：在輸入框的第一行按 ↑ 時，Rota 會讀 CLI 自己的 prompt 紀錄，和在 CLI 裡按 ↑ 時讀的是同一個檔案：Claude Code 是 `~/.claude/history.jsonl` 裡這個專案的紀錄，Codex 是 `CODEX_HOME`（沒有設定時是 `~/.codex`）裡的 `history.jsonl`。只讀檔案最後 1 MB、最多 200 筆，只放在記憶體裡，不寫入、不複製，也不記錄。

## 資料放在哪裡

全部在你的 Mac 上：

```
~/Library/Application Support/Shiftboard/
```

（「Shiftboard」是 Rota 的內部名稱。）

Rota 沒有伺服器，也沒有任何使用統計或錯誤回報。跟網路有關的只有這些：

- **檢查 Claude 用量**（只在你開啟「帳號用量」時）：由 Claude Code 自己的 status line 提供，Rota 只讀取用量數字；
- **讀取 Codex 用量**：透過你電腦上的 Codex CLI，Rota 本身不直接連網；
- **無線執行 App 到手機**（只在你使用時）：透過區域網路連到你自己的 iPhone 或 Android 手機；
- **自動更新**（可以在「設定 → 進階與診斷 → 更新」關閉）：開啟 Rota 時向 GitHub 讀取版本資訊；有新版本時從 GitHub 下載安裝檔，下載後先驗證簽章才會安裝。跟一般下載一樣，GitHub 會看到你的 IP 位址和 Rota 的版本，不會傳送其他資料。

## 會改動的設定檔

| 檔案 | 改動 |
|---|---|
| `~/.claude/settings.json` | 加入 Rota 的 hook 條目；開啟帳號用量時，另外加入 status line |
| `~/.codex/hooks.json` | 加入 Rota 的 hook 條目 |

每次修改前都會先備份。按「解除安裝」只會移除 Rota 自己的條目。

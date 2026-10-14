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

## 資料放在哪裡

全部在你的 Mac 上：

```
~/Library/Application Support/Shiftboard/
```

（「Shiftboard」是 Rota 的內部名稱。）

Rota 沒有伺服器，也沒有任何使用統計或錯誤回報。跟網路有關的只有這些：

- **檢查 Claude 用量**（只在你開啟「帳號用量」時）：由 Claude Code 自己的 status line 提供，Rota 只讀取用量數字；
- **讀取 Codex 用量**：透過你電腦上的 Codex CLI，Rota 本身不直接連網；
- **無線執行 App 到手機**（只在你使用時）：透過區域網路連到你自己的 iPhone 或 Android 手機。

## 會改動的設定檔

| 檔案 | 改動 |
|---|---|
| `~/.claude/settings.json` | 加入 Rota 的 hook 條目；開啟帳號用量時，另外加入 status line |
| `~/.codex/hooks.json` | 加入 Rota 的 hook 條目 |

每次修改前都會先備份。按「解除安裝」只會移除 Rota 自己的條目。

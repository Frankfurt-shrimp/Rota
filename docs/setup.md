# 第一次設定

[← 回到首頁](../README.md) ｜ [English](setup.en.md)

Rota 透過 Claude Code 與 Codex 的 **hook** 知道 AI 什麼時候開始、什麼時候結束一輪工作。hook 是這兩個 CLI 內建的功能：在特定時間點執行一個小程式。這一頁說明設定時會發生什麼事。

## 1. 先準備好 AI CLI

至少安裝並登入其中一個：

- **Claude Code**：在終端機執行 `claude`，能正常對話就可以。
- **Codex CLI**：在終端機執行 `codex`，能正常對話就可以。

## 2. 啟用整合

第一次開啟 Rota 時會出現設定面板，按「**啟用整合…**」。也可以之後到「**設定 → Agent 整合**」再設定。

按下之前，Rota 會先列出它要做的所有事，等你確認：

| 會做的事 | 說明 |
|---|---|
| 在 `~/.claude/settings.json` 加入條目 | 只附加 Rota 自己的條目；你原本的設定與其他 hook 不變 |
| 在 `~/.codex/hooks.json` 加入條目 | 同上；如果這個檔案原本不存在，Rota 會建立一個只有自己條目的檔案（只有你能讀寫） |
| 先備份 | 每個檔案在修改前都會備份；寫入失敗時會自動還原 |
| 安裝一個背景小工具 | 放在 `~/Library/Application Support/Shiftboard/bin/`，hook 會呼叫它記錄「開始／結束」的時間 |

> Rota 只記錄時間點，不讀取 prompt、程式碼或對話內容。詳見[隱私](privacy.md)。

## 3. Codex：核准新的 hook

Codex 會要求你核准新加入的 hook。設定完成後，在 Codex 裡執行一次：

```
/hooks
```

照畫面指示核准 Rota 的條目即可。之後 Rota 更新了 hook 的話，Codex 也可能再請你核准一次。

## 4. 確認設定成功

在 Claude Code 或 Codex 送出一次真正的 prompt。Rota 收到第一個事件後會自動完成檢查，「設定 → Agent 整合」中的狀態會變成**已啟用**。

## 5. 開始使用

1. 側邊欄按「＋」新增專案，選擇專案資料夾。
2. 在看板按「新增卡片」。
3. 在專案終端機輸入 `claude` 或 `codex`。
4. 終端機上方跳出提議時，選一張卡片，再選「**規格**」或「**實作**」。

如果不想看到連結提議，可以到「設定 → 終端機」關閉「在 Rota 終端機啟動的 Session 建議連結卡片」。

## 選用功能

| 功能 | 需要 |
|---|---|
| 帳號用量（在 Rota 顯示 Claude 的用量） | 在「設定 → Agent 整合」另外開啟；會安裝 Rota 的 Claude Code status line |
| 從工具列執行 iOS App | Xcode；實機需要先在 Xcode 配對過 |
| 從工具列執行 Android App | Android Studio，或 Android SDK 與 JDK |
| Android 不接線執行 | 第一次用 USB 接上手機，在目的地選單選「不接線使用」 |

# 完全移除 Rota

[← 回到首頁](../README.md) ｜ [English](uninstall.en.md)

請**照順序**做。如果先刪掉 App，Rota 加入的 hook 條目會留在 Claude Code 和 Codex 的設定檔裡。

## 1. 解除安裝整合

1. 打開 Rota，到「**設定 → Agent 整合**」。
2. 在 Claude Code 與 Codex 下各按一次「**解除安裝**」。
3. 如果開啟過「帳號用量」，也一併關閉，Rota 的 status line 會被移除。

Rota 只會移除自己的條目，你自己的其他 hook 與設定維持原樣。如果 `~/.codex/hooks.json` 當初是 Rota 建立的，而且裡面只有 Rota 的條目，這個檔案會被刪除。

## 2. 刪除 App

結束 Rota，把「應用程式」裡的 `Rota.app` 移到垃圾桶。

## 3.（選擇性）刪除資料

如果也不需要專案、卡片與紀錄，在 Finder 按 ⇧⌘G，輸入下面的路徑，把整個資料夾移到垃圾桶：

```
~/Library/Application Support/Shiftboard
```

另外還有幾個小東西也可以刪：

- 偏好設定：`~/Library/Preferences/com.franklin.shiftboard.plist`
- 執行 App 的記錄：放在上面那個資料夾的 `Runs/` 裡，會一起刪掉。

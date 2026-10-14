# 常見問題

[← 回到首頁](../README.md) ｜ [English](faq.en.md)

## 安裝與更新

<details>
<summary>打開時 macOS 說「無法打開」或「無法驗證開發者」</summary>

請確認你下載的是 [Releases](../../../releases/latest) 頁面上的 `.dmg`。正式版本都經過 Apple 公證，正常情況下不會被擋。如果還是出現這個訊息，請[回報問題](../../../issues/new/choose)，並附上截圖。
</details>

<details>
<summary>Rota 顯示「找到舊版 Roundelay」</summary>

Rota 以前叫 Roundelay。兩者會共用同一份資料，同時保留可能會開錯 App。請按「在 Finder 顯示」，把舊的 `Roundelay.app` 移到垃圾桶。你的資料不會受影響。
</details>

<details>
<summary>更新後出現「整合需要更新」</summary>

新版本的 Rota 可能帶有新的 hook 或新的背景小工具。按「更新…」，確認清單後按「全部更新」即可。每個檔案都會先備份。更新 Codex 後，可能需要在 Codex 裡執行一次 `/hooks` 核准。
</details>

## 連結卡片

<details>
<summary>開了 <code>claude</code> 或 <code>codex</code>，但沒有跳出連結提議</summary>

請依序確認：

1. 是在 **Rota 的專案終端機**中啟動的。一般的「終端機」App 不會提議。
2. 「設定 → Agent 整合」中，對應的 AI 是**已啟用**，而且沒有「需要更新」。
3. Codex 的 hook 已經用 `/hooks` 核准過。
4. 「設定 → 終端機」裡的連結提議沒有被關掉。
5. **開啟 Codex 時，Rota 會先問要連結到哪張卡片；送出第一個 prompt 後自動完成。** 如果按了「稍後」，可以從終端機右上角「⋯」的「Session 配對」重新叫出。Claude Code 則是開啟時就直接提議。
6. Rota 終端機中的 Codex 預設以**獨立模式**（`--no-daemon`）執行，所以同一個專案開兩個 Codex 也分得出是哪個終端機。這個模式下，每個 Codex 開著時各自佔用記憶體，結束就釋放；`codex agents` 看不到這些 Session；結束時選「留在背景」，工作可能不會繼續。目前只支援 zsh。想用共用模式，可以在「設定 → 終端機」關掉，或在 Rota 終端機輸入 `command codex`。共用模式下，兩個終端機幾乎同時送出 prompt 時，Rota 無法判斷，會把 Session 留在「未分配」，請手動配對。在其他終端機 App 中、同一個專案資料夾開 Codex 時，Rota 可能會在你的 Rota 終端機中提議它，請看清楚提議中的 Session ID。
</details>

<details>
<summary>更新 Rota 之後，Codex 要怎麼重新啟用</summary>

1. 打開 Codex，輸入 `/hooks`，核准 Rota 的 hook。
2. 用 `/exit` 結束 Codex，**再重新開一次** `codex`。核准之前就開著的 Codex 不會執行新的 hook，所以要重開。
3. 送出一個 prompt。Rota 收到後會自動把整合標為已啟用，並提議連結卡片，不用再到設定按確認。
</details>

<details>
<summary>怎麼結束 Codex CLI</summary>

- 輸入 **`/exit`**（或 `/quit`），最直接。
- 或按 **Ctrl+C 兩下**：第一下會中斷目前的動作，並提示「再按一次結束」，約 1 秒內再按一下就會結束。Ctrl+D 也一樣，要按兩下。
- **Esc 只會中斷 AI 正在做的事，不會結束 Codex。**
- 結束時如果還有工作在跑，Codex 會問你要取消、留在背景繼續，還是停止並結束。選「在背景繼續」時，Rota 會把那個 Session 視為已結束。
</details>

<details>
<summary>連錯卡片或選錯角色了</summary>

打開卡片，在 Session 區塊中取消連結，再重新連結。取消連結只會移除 Rota 的紀錄，不會影響 AI 的 Session 本身。
</details>

## 卡片狀態

<details>
<summary>卡片一直顯示「正在等待背景工作」</summary>

AI 還有背景工作在跑，例如 subagent 或背景指令。等它們結束，卡片就會完成。只是在等外部事件的「監看」不會擋住卡片，卡片上會顯示「監看中」。
</details>

<details>
<summary>完成時的光暈顏色代表什麼</summary>

顏色代表**完成的那個 Session 的角色**：規格是藍色、實作是橘色。沒有連結卡片的 Session，Codex 視為規格、Claude Code 視為實作。可以在「設定 → 外觀與版面」關閉光暈，或改成只對已連結卡片的 Session 顯示。
</details>

## 執行 App

<details>
<summary>iPhone 在目的地選單中是灰的，寫「需要 iOS xx」</summary>

App 的最低系統版本比手機新。請在 Xcode 的 target → General → Minimum Deployments 調低版本，或更新手機，然後在目的地選單按「重新整理」。
</details>

<details>
<summary>Android 不接線執行</summary>

1. 用 USB 接上手機，在目的地選單選「不接線使用」。
2. 拔線，讓 Mac 連上手機的熱點，或跟手機連同一個 Wi-Fi。
3. 選擇手機，按 ▶︎。

手機重新開機後要再插一次線。同一個 Wi-Fi 時，也可以用「用配對碼配對 Android 裝置…」。三星手機若開著「自動封鎖程式（Auto Blocker）」，可能會擋住偵錯功能。
</details>

<details>
<summary>選了 Android 專案資料夾，卻說不是 App</summary>

請選擇有 `settings.gradle(.kts)` 和 `gradlew` 的那一層。Rota 會自動往上或往下找。如果整個專案就是一個 App（沒有 `:app` 子模組），Rota 會顯示為「根專案」。
</details>

## 其他

<details>
<summary>怎麼回報問題</summary>

到 [Issues](../../../issues/new/choose) 選「回報問題」，附上 macOS 版本、Rota 版本與截圖。請勿貼上 API key、token 或其他私密資訊。
</details>

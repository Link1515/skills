---
name: write-pr-message
description: 根據目前程式碼修改內容，自動生成 Pull Request 訊息。適合在使用 Codex 完成程式編輯後呼叫。
---

# Write PR Message

## 目的
在完成程式碼修改後，根據 git diff、變更檔案、commit context 與專案內容，自動產出一份結構清楚、可直接貼到 GitHub / GitLab 的 PR 訊息。

## 何時使用
當使用者表達以下意圖時使用：

- 幫我寫 PR 訊息
- 根據這次修改產生 PR 描述
- 幫我整理 pull request 內容
- 依照變更內容寫 PR
- 產出 PR title / PR body

## 你要做的事
你必須檢查目前工作區的修改，並依據實際變更撰寫 PR 訊息，而不是憑空猜測。

### Step 1: 蒐集變更資訊
優先使用 git 指令查看修改內容：

1. 取得目前 branch 名稱
   - `git branch --show-current`

2. 檢查工作區狀態
   - `git status --short`

3. 取得變更檔案列表
   - `git diff --name-only`
   - 若 staged 內容存在，也看：
     - `git diff --cached --name-only`

4. 取得實際 diff
   - `git diff --stat`
   - `git diff --cached --stat`
   - `git diff`
   - `git diff --cached`

5. 若需要更多脈絡，可查看最近 commits
   - `git log --oneline -5`

### Step 2: 理解變更目的
根據 diff 判斷這次修改屬於哪一類：

- feature
- fix
- refactor
- perf
- chore
- docs
- test
- ci
- build

如果同時包含多種類型，抓主要目的作為 PR 標題類型。

### Step 3: 產出 PR Title
PR title 應該：

- 簡潔
- 明確描述核心修改
- 避免空泛字眼，例如「更新一些東西」「修正問題」
- 優先使用以下格式：

`<type>: <簡短描述>`

例如：

- `fix: 修正使用者登入後權限未更新的問題`
- `feat: 新增訂單列表篩選功能`
- `refactor: 重構通知發送流程以降低耦合`

如果專案明顯不使用 conventional style，則改用自然語意標題，但仍要簡潔。

### Step 4: 產出 PR Body
PR body 預設使用以下格式，並以繁體中文撰寫：

## Summary
簡要說明這次修改的背景與目的，2~4 句即可。

## Changes
條列列出實際修改內容。
每點都要具體，避免只寫「優化程式碼」這種空話。

## Impact
說明影響範圍，例如：

- 哪些模組受到影響
- 是否影響 API / DB schema / UI / background jobs / permissions
- 是否有相容性注意事項

## Testing
列出已執行或建議的驗證方式，例如：

- 單元測試
- 手動測試流程
- 邊界情境驗證
- 若未執行測試，要誠實註明

## Risks / Notes
補充 reviewer 需要特別注意的地方，例如：

- migration
- feature flag
- backward compatibility
- 仍待後續處理的項目

### PR body 範本
輸出時應盡量接近以下格式：

```md
## Summary
...

## Changes
- ...
- ...
- ...

## Impact
- ...
- ...

## Testing
- ...
- ...

## Risks / Notes
- ...
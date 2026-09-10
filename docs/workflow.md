# GitHub 協作流程

工作、成果與狀態以本 repository 的 Issue、PR 及日報為共同來源。

## 任務欄位

Issue 開頭使用以下純文字欄位。這些欄位是狀態依據；標籤可作輔助，初始化不依賴額外標籤或 GitHub Projects 設定。

```text
Type: task
Task-ID: OPS-001
Executor: claude-cowork
Status: ready
Priority: P0
Task-Budget-Minutes: 30
Depends-On: none
Target: 首次執行批次
```

角色為 `claude-cowork`、`human`、`director`。GitHub Assignee 只填經確認的實際帳戶；角色欄位已足以供領單。

| Status | 意義 | 更新方式 |
| --- | --- | --- |
| backlog | 未完成排程或依賴尚未滿足 | 總監整理 |
| ready | 範圍與驗收明確、依賴已完成 | 總監啟用 |
| doing | 已領單執行 | 工程師留言後更新 |
| blocked | 缺少環境、資料或決策 | 工程師說明阻塞，總監處理 |
| review | 交付可檢查成果，等待驗收 | 工程師提交後更新 |
| done | 驗收及必要整合完成 | 總監核對後關閉 Issue |

每個 Type 為 task 的 Issue 只保留一個 Status 欄位。journal 與 meeting-log 不進入任務佇列。

## 領單、交付與修正

- 每位工程師同時只處理一項任務。先檢查同一 Issue 是否已有執行紀錄與 PR，接續既有工作。
- 領單時先留言，記錄日期、批次識別與分支，再設為 doing。PR 引用 Issue，附實際測試、重跑步驟及限制。
- 需要真人設備或環境實測的部分單獨列出；雲端模擬結果與實際設備結果分開記錄。
- PR 提交後為 review。總監審查、真人補足必要驗證，通過且完成整合後才關閉任務。
- 需要修正時留下具體差距，再重新安排可執行工作；超出首版範圍的需求另開 backlog。
- 每天兩小時為總預算。受阻或到達工作單時間時先交付現況，標明未完成與下一個可驗證步驟。

## 日報及例會

每位工程師一張固定日報 Issue，依 Asia/Taipei 的日期追加留言；使用 [日報範本](templates/daily-report.md)。同一天再次執行時報告當日累計投入，避免把每一批次當作新的兩小時。

例會固定 Issue 記錄當次成果、風險、最多三項優先工作、最多兩項待決策事項，以及老闆實際回覆與後續負責人。沒有回覆的決策標記待決策。

日報串、例會串與任務位置見 [工作入口](work-items.md)。

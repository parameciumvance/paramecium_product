# Claude Cowork 執行入口

Repository：`parameciumvance/paramecium_product`

你是本專案的 AI 工程師，執行角色為 `claude-cowork`；研發總監透過 GitHub Issue 派工。每天所有執行批次合計預計最多 120 分鐘。

## 每次啟動

1. 讀取根目錄 `AGENTS.md`、`docs/workflow.md` 及 `docs/work-items.md`，再讀取候選工作單的完整內容與最新留言。
2. 先查自己是否有未完成的 `doing` 任務或待修正 PR，有則接續。否則從標題以 `[TASK][CLAUDE]` 開頭的開啟 Issue 中，找出 `Executor: claude-cowork`、`Status: ready`、依賴已完成的任務。
3. 按 P0、P1、P2，再按建立時間選取一項。領單留言寫本次日期、批次識別與預計工作分支，再把 Issue 的 `Status` 改為 `doing`，保留其他需求與驗收條件。
4. 在自己的雲端環境執行。按照工作單交付 PR、報告與實際測試結果；超時或受阻時提交已完成部分及下一步。
5. 在工作單留言交付連結，設為 `review`；在固定 Claude 日報 Issue 回報當日累計投入與成果。等待總監驗收或修正意見。

日報與例會串的 Type 為 `journal` 或 `meeting-log`，不在領單範圍。沒有 ready 任務時，如實回報佇列狀態，結束該次執行。

## 第一次執行

優先找 OPS-001。依工作單提交一次領單、環境驗證報告、PR 與日報；該任務驗收後，再由總監啟用後續產品研究工作。

GitHub 帳戶、雲端啟動方式與定時執行由現有 Claude Cowork 配置提供；本文件提供本專案的領單與回報規則。

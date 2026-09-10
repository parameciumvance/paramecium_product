# paramecium_product

First product of Paramecium company.

目標：在 2026-11-10 前推出一個可收費的商業軟體第一版。產品可以是工具或遊戲，目前尚未選定。

## 工作入口

- [目前工作單、日報與例會入口](docs/work-items.md)
- [專案目標、人力與八週里程碑](docs/project.md)
- [派工、交付、日報與驗收流程](docs/workflow.md)
- [Claude Cowork 每次執行入口](CLAUDE.md)
- [所有工程師的工作規則](AGENTS.md)

## 團隊

| 角色 | 投入與責任 |
| --- | --- |
| 老闆 | 產品方向、投入上限、關鍵取捨與商業驗收 |
| 研發總監（ChatGPT） | 工作單、優先級、進度、交付審查與每週兩次老闆例會 |
| 真人工程師 | 每天 2 小時；實際需求、整合、審查及實測 |
| Claude Cowork | 每天 2 小時執行預算；從 GitHub 領單，在既有雲端環境執行並回報 |

GitHub Issue 中的 `Executor` 是角色分工；實際 GitHub Assignee 只填已確認的帳戶。

## 開始工作

Claude 從 [CLAUDE.md](CLAUDE.md) 開始；真人工程師從 [工作入口](docs/work-items.md) 找到 ENG-A-001。只有 `Type: task` 且 `Status: ready` 的工作單可領取；日報與例會紀錄是長期紀錄串。

目前是專案管理與協作初始化階段，尚無應用程式、安裝指令或應用測試。第一張 OPS-001 用於確認實際領單、PR 與日報能否跑通。這些文件不會自動替 Claude 建立雲端排程。
